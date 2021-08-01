<template>
  <div class="finger">
    <div class="finger__item"
        @click="toggle"
      >
      <i class="las la-hand-point-left"
          :class="iconStyle"
        >
      </i>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    isOn: Boolean
  },
  computed: {
    iconStyle () {
      return {
        'on-color': this.isOn,
        'off-color': !this.isOn
      };
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
  .on-color {
    color: #134e6f;
    opacity: 1;
  }

  .off-color {
    opacity: 0;
  }

  .finger {
    width: 22px;  height: 22px;
  }
    .finger__item {
      /* background-color: thistle; */
      font-size: 26px;
      width: 26px;  height: 26px;
      transform: rotate(90deg);
    }
</style>

