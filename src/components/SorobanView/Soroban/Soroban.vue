<template>
  <div class="soroban">
    <Rod class="soroban__rod"
        v-for="(digit, idx) in digits"
        :key="idx"
      />
  </div>
</template>

<script>
import Rod from "./Rod.vue"

export default {
  components: {
    Rod,
  },
  data () {
    return {
      rodsNumber: 13,
      digits: [],
    };
  },
  beforeMount () {
    this.digits = Array(this.rodsNumber)
      .fill(0);
  }
}
</script>

<style scoped>
  .soroban {
    background-color: turquoise;
    width: 400px;
    padding: 12px 8px;
    border-radius: 10px;

    /* text-align: center; */
    
    display: flex;
    justify-content: space-between;
  }

  .soroban__rod {
    /* background-color: tomato; */
    margin: 0 3px;
  }
</style>

