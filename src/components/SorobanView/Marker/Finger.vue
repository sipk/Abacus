<template>
  <div class="finger">
    <div class="finger__item"
        v-for="(digit, idx) in digits"
        :key="idx"
        @click="toggle(idx)"
      >
      <i class="las la-hand-point-left"
          :class="indicatorStyles(idx)"
        >
      </i>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      rodsNumber: 13,
      digits: [],
    };
  },
  beforeMount () {
    this.digits = Array(this.rodsNumber)
      .fill(false);
    this.digits[0] = true;
  },
  methods: {
    indicatorStyles (idx) {
      return {
        'gold-mid': this.digits[idx],
        'gray-lighter': !this.digits[idx]
      };
    },
    toggle (idx) {
      console.log('toggled');
      this.digits = Array(this.rodsNumber)
        .fill(false);
      this.digits[idx] = true;
    }
  }
}
</script>

<style scoped>
  @import url("https://maxst.icons8.com/vue-static/landings/line-awesome/line-awesome/1.3.0/css/line-awesome.min.css");
  @import url("https://use.fontawesome.com/releases/v5.6.1/css/all.css");

  .gold-mid{
    color: #666666;
    opacity: 1;
  }

  .gray-lighter{
    opacity: 0;
  }

  .finger {
    width: 400px;
    padding: 4px 4px 8px 12px;
    display: flex;
    justify-content: space-between;
  }
    .finger__item {
      /* background-color: thistle; */
      font-size: 26px;
      height: 26px;
      transform: rotate(90deg);
    }
</style>

