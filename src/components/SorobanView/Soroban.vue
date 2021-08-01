<template>
  <div class="soroban">
    <RodContainer class="soroban__rod"
        v-for="(value, index) in values"
        :key="index"
        :id="index"
        :isPinOn="isPinOn[index]"
        :value="values[index]"
        :hasPoint="hasPoint(index)"
        :isFingerOn="isFingerOn[index]"
        @tapPin="tapPin"
        @valueChanged="valueChanged"
        @tapFinger="tapFinger"
      />
    <button class="soroban__clear"
        @click="clear"
      >
      <i class="las la-undo-alt"
          :class="iconStyle"
        >
      </i>
    </button>
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
      digitsNumber: 23,
      isPinOn: [],
      values: [],
      isFingerOn: []
    };
  },
  computed: {
    iconStyle () {
      return 'on-color';
    }
  },
  beforeMount () {
    this.isPinOn = Array(this.digitsNumber)
      .fill(false);
    this.isPinOn[0] = true;
    this.values = Array(this.digitsNumber)
      .fill(0);
    this.isFingerOn = Array(this.digitsNumber)
      .fill(false)
    this.isFingerOn[0] = true;
  },
  methods: {
    hasPoint (index) {
      return index % 3 === 2;
    },
    tapPin (id) {
      this.isPinOn.length = 0;
      this.isPinOn = Array(this.digitsNumber)
        .fill(false);
      this.isPinOn[id] = true;
    },
    tapFinger (id) {
      this.isFingerOn.length = 0;
      this.isFingerOn = Array(this.digitsNumber)
        .fill(false);
      this.isFingerOn[id] = true;
    },
    valueChanged ({ id, value }) {
      this.values[id] = value;
    },
    clear () {
      this.values.length = 0;
      this.values = Array(this.digitsNumber)
        .fill(0);
    }
  },
}
</script>

<style scoped>
  .on-color {
    color: #ff6150;
    opacity: 1;
  }

  .soroban {
    display: flex;
    align-items: center;
    justify-content: center;
  }
    .soroban__rod {
      margin: 0 3px;
    }
    .soroban__clear {
      color: #ff6150;
      background-color: #ff615033;
      font-size: 28px;
      width: 66px; height: 66px;
      margin-left: 24px;
      border-radius: 50%;
      border: none;

      display: flex;
      align-items: center;
      justify-content: center;
    }
</style>

