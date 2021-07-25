<template>
  <h1>drawing</h1>
  <canvas id="canvas"
    ref="canvas"
    @mousedown="onMouseDown"
    @mousemove="onMouseMove"
    @mouseup="onMouseUp"
  >
  </canvas>
</template>

<script>
  export default {
    data () {
      return {
        size: 2,
        isPressed: false,
        color: 'black',
        offset: [],
      };
    },
    mounted () {
      const canvas = this.$refs.canvas;
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
      }
    }
  }
</script>

<style scoped>
  #canvas {
    border: 2px solid steelblue;
  }
</style>