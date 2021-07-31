<template>
  <div class="soroban">
    <RodContainer class="soroban__rod"
        v-for="(digit, index) in digits"
        :key="index"
        :pinID="index"
        :isPinOn="isPinOn[index]"
        :hasPoint="hasPoint(index)"
        :fingerID="index"
        :isFingerOn="isFingerOn[index]"
        @tapPin="tapPin"
        @tapFinger="tapFinger"
      />
  </div>
</template>

<script>
import RodContainer from './RodContainer.vue'

export default {
  components: {
    RodContainer,
  },
  data () {
    return {
      rodsNumber: 23,
      isPinOn: [],
      digits: [],
      isFingerOn: []
    };
  },
  beforeMount () {
    this.isPinOn = Array(this.rodsNumber).fill(false);
    this.isPinOn[0] = true;
    this.digits = Array(this.rodsNumber)
      .fill(0);
    this.isFingerOn = Array(this.rodsNumber).fill(false)
    this.isFingerOn[0] = true;
  },
  methods: {
    hasPoint (index) {
      return index % 3 === 2;
    },
    tapPin (id) {
      this.isPinOn.length = 0;
      this.isPinOn = Array(this.rodsNumber).fill(false);
      this.isPinOn[id] = true;
    },
    tapFinger (id) {
      this.isFingerOn.length = 0;
      this.isFingerOn = Array(this.rodsNumber).fill(false);
      this.isFingerOn[id] = true;
    }
  },
}
</script>

<style scoped>
  .soroban {
    display: flex;
  }

  .soroban__rod {
    margin: 0 3px;
  }
</style>

