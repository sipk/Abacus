<template>
  <div class="drawing">
    <canvas class="drawing__canvas"
        id="canvas"
        ref="canvas"
        @mousedown="onMouseDown"
        @mousemove="onMouseMove"
      >
    </canvas>
    <div class="drawing__tool">
      <button class="drawing__erase"
          :style="eraseButtonStyle"
          @click="erase"
        >
        <i class="las la-eraser"></i>
      </button>
      <button class="drawing__trash"
          @click="trash"
        >
        <i class="las la-trash"></i>
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        size: 2,
        isDrawing: false,
        color: '#134e6f',
        offset: [],
        isErasing: false
      };
    },
    computed: {
      eraseButtonStyle () {
        return this.isErasing 
          ? { backgroundColor: "#134e6f", color : "#fff" }
          : { backgroundColor: "#134e6f33", color : "#134e6f" };
      }
    },
    mounted () {
      window.addEventListener('resize', this.onResize);
      this.onResize();

      window.addEventListener('mouseup', this.onMouseUp);

      const canvas = this.$refs.canvas;
      this.ctx = canvas.getContext('2d');
    },
    methods: {
      onResize () {
        const canvas = this.$refs.canvas;
        const canvasWidth = document.getElementById('canvas').clientWidth;
        const canvasHeight = document.getElementById('canvas').clientHeight;
        canvas.width = canvasWidth;
        canvas.height = canvasHeight;
      },
      onMouseDown (e) {
        this.isDrawing = true;
        this.offset = [e.offsetX, e.offsetY];
      },
      onMouseUp (e) {
        this.isDrawing = false;
        this.offset.length = 0;
      },
      onMouseMove (e) {
        if (this.isDrawing) {
          const offset = [e.offsetX, e.offsetY];
          this._drawCircle(offset);
          this._drawLine(this.offset, offset);
          this.offset = offset;
        }
      },
      _drawCircle (offset) {
        const [x, y] = offset;
        this.ctx.beginPath();
        const radius = this.isErasing ? 6 : this.size;
        this.ctx.arc(x, y, radius, 0, Math.PI * 2);
        this.ctx.fillStyle = this.color;
        this.ctx.fill();
      },
      _drawLine (offset1, offset2) {
        const [x1, y1] = offset1;
        const [x2, y2] = offset2;
        this.ctx.beginPath();
        this.ctx.moveTo(x1, y1);
        this.ctx.lineTo(x2, y2);
        this.ctx.strokeStyle = this.color;
        this.ctx.lineWidth = this.isErasing ? 12 : this.size * 2;
        this.ctx.stroke();
      },
      erase () {
        this.isErasing = !this.isErasing;
        this.ctx.globalCompositeOperation = this.isErasing
          ? 'destination-out'
          : 'source-over';
      },
      trash () {
        this.ctx.clearRect(
          0, 0, 
          this.ctx.canvas.clientWidth, this.ctx.canvas.clientHeight
        );
      }
    },
    beforeUnmount () {
      window.removeEventListener('resize', this.onResize);
    }
  }
</script>

<style scoped>
  .drawing {
    display: flex;
    align-items: center;
    justify-content: center;

    /* background-color: blanchedalmond; */
  }
    .drawing__canvas {
      width: 100%;
      max-height: 240px;
      border: 1px solid #ccc;

      cursor: pointer;
    }
    .drawing__tool {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-direction: column;
      margin-left: 24px;
      position: relative;

      /* background: black; */
      width: 80px;  height: 160px;
    }
      .drawing__erase,
      .drawing__trash {
        background-color: #ff615033;
        color: #ff6150;
        font-size: 32px;
        width: 66px; height: 66px;
        border-radius: 50%;
        border: none;

        display: flex;
        align-items: center;
        justify-content: center;

        cursor: pointer;
      }
</style>