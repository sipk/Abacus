<template>
  <div class="drawing">
    <canvas class="drawing__canvas"
        id="canvas"
        ref="canvas"
        @mousedown="onMouseDown"
        @mousemove="onMouseMove"
        @mouseup="onMouseUp"
      >
    </canvas>
    <button class="drawing__clear"
        @click="clear"
      >
      <i class="las la-backspace"
          :class="iconStyle"
        >
      </i>
    </button>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        size: 2,
        isPressed: false,
        color: '#134e6f',
        offset: [],
      };
    },
    computed: {
      iconStyle () {
        return 'on-color';
      }
    },
    mounted () {
      const canvas = this.$refs.canvas;
      const canvasWidth = document.getElementById('canvas').clientWidth;
      const canvasHeight = document.getElementById('canvas').clientHeight;
      canvas.width = canvasWidth;
      canvas.height = canvasHeight;
      this.ctx = canvas.getContext('2d');
    },
    methods: {
      onMouseDown (e) {
        this.isPressed = true;
        this.offset = [e.offsetX, e.offsetY];
      },
      onMouseUp (e) {
        this.isPressed = false;
        this.offset.length = 0;
      },
      onMouseMove (e) {
        if (this.isPressed) {
          const offset = [e.offsetX, e.offsetY];
          this._drawCircle(offset);
          this._drawLine(this.offset, offset);
          this.offset = offset;
        }
      },
      _drawCircle (offset) {
        const [x, y] = offset;
        this.ctx.beginPath();
        this.ctx.arc(x, y, this.size, 0, Math.PI * 2);
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
        this.ctx.lineWidth = this.size * 2;
        this.ctx.stroke();
      },
      clear () {
        this.ctx.clearRect(
          0, 0, 
          this.ctx.canvas.clientWidth, this.ctx.canvas.clientHeight
        );
      }
    }
  }
</script>

<style scoped>
  .on-color {
    color: #ff6150;
    opacity: 1;
  }

  .drawing {
    display: flex;
    align-items: center;
    justify-content: center;
  }
    .drawing__canvas {
      width: 70%;
      max-height: 240px;
      border: 1px solid #ccc;
    }
    .drawing__clear {
      background-color: #ff615033;
      font-size: 32px;
      width: 66px; height: 66px;
      margin-left: 24px;
      border-radius: 50%;
      border: none;

      display: flex;
      align-items: center;
      justify-content: center;
    }
</style>