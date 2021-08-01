<template>
  <div class="soroban">
    <RodContainer class="soroban__rod"
        v-for="(value, index) in values"
        :key="index"
        :id="index"
        :isPinOn="isPinOn(index)"
        :pinColor="pinColor(index)"
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
      pins: [
        { index: 0, color: '#134e6f' },
        { index: 1, color: '#ff6150' },
        { index: 2, color: '#1ac0c6' },
      ],
      values: [],
      isFingerOn: []
    };
  },
  computed: {
    iconStyle () {
      return 'on-color';
    },
  },
  beforeMount () {
    this.values = Array(this.digitsNumber)
      .fill(0);
    this.isFingerOn = Array(this.digitsNumber)
      .fill(false)
    this.isFingerOn[0] = true;
  },
  methods: {
    isPinOn (index) {
      return this.pins.some((pin) => {
        return pin.index === index;
      });
    },
    pinColor (index) {
      const pin = this.pins.find((pin) => {
        return pin.index === index;
      });
      return pin ? pin.color : '';
    },
    hasPoint (index) {
      return index % 3 === 2;
    },
    tapPin (id) {
      this.pins[0].index = id;
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

