<template>
  <div class="pin">
    <div class="pin__item"
        v-for="(digit, idx) in digits"
        :key="idx"
        @click="toggle(idx)"
      >
      <div class="pin__circle"
          :class="indicatorStyles(idx)"
        >
      </div>
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
  .gold-mid{
    color: red;
    opacity: 1;
  }

  .gray-lighter{
    opacity: 0;
  }

  .pin {
    width: 400px;
    padding: 4px 12px;
    display: flex;
    justify-content: space-between;
  }
    .pin__item {
      width: 20px;  height: 20px;

      display: flex;
      align-items: center;
      justify-content: center;
    }
    .pin__circle {
      background-color: red;
      width: 10px; height: 10px;
      border-radius: 5px;
    }
</style>

