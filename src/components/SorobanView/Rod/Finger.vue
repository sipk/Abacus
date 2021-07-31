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
    id: Number,
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
      this.$emit('input', this.id);
    }
  }
}
</script>

<style scoped>
  @import url("https://maxst.icons8.com/vue-static/landings/line-awesome/line-awesome/1.3.0/css/line-awesome.min.css");
  @import url("https://use.fontawesome.com/releases/v5.6.1/css/all.css");

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

