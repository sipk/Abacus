<template>
  <div class="pin"
      @click="toggle"
    >
    <div class="pin__dot"
        :style="dotStyle"
      >
    </div>
  </div>
</template>

<script>
export default {
  props: {
    isOn: Boolean,
    color: String,
  },
  computed: {
    dotStyle () {
      return {
        backgroundColor: this.color,
        opacity: this.isOn ? 1 : 0
      }
    },
  },
  methods: {
    toggle () {
      this.$emit('input');
    }
  }
}
</script>

<style scoped>
  .pin {
    width: 22px;  height: 22px;

    display: flex;
    align-items: center;
    justify-content: center;

    cursor: pointer;
  }
    .pin__dot {
      /* background-color: #134e6f; */
      width: 10px; height: 10px;
      border-radius: 5px;
    }
</style>

