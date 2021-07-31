<template>
  <div class="pin"
      @click="toggle"
    >
    <div class="pin__dot"
        :class="dotStyle"
      >
    </div>
  </div>
</template>

<script>
export default {
  props: {
    id: Number,
    isOn: Boolean
  },
  computed: {
    dotStyle () {
      return {
        'on-color': this.isOn,
        'off-color': !this.isOn
      };
    },
  },
  methods: {
    toggle () {
      this.$emit('input', this.id);
    }
  }
}
</script>

<style scoped>
  .on-color {
    /* color: #ff6150; */
    color: #134e6f;
    opacity: 1;
  }

  .off-color {
    opacity: 0;
  }

  .pin {
    width: 22px;  height: 22px;

    display: flex;
    align-items: center;
    justify-content: center;
  }
    .pin__dot {
      /* background-color: #ff6150; */
      background-color: #134e6f;
      width: 10px; height: 10px;
      border-radius: 5px;
    }
</style>

