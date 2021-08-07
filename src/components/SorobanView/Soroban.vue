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
        :isFingerOn="isFingerOn(index)"
        @tapPin="tapPin"
        @valueChanged="valueChanged"
        @tapFinger="tapFinger"
      />
    <div class="soroban__tool">
      <PinSelector class="soroban__pin-selector" 
          :options="pinColors"
          :selected="selectedPinColor"
          @valueChanged="selectPinColor"
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
  </div>
</template>

<script>
import RodContainer from './RodContainer.vue'
import PinSelector from './PinSelector.vue'

export default {
  components: {
    RodContainer,
    PinSelector
  },
  data () {
    return {
      digitsNumber: 23,
      pins: [
        { index: 0, color: '#134e6f' },
        { index: 1, color: '#ff6150' },
        { index: 2, color: '#1ac0c6' },
      ],
      selectedPinColor: '#134e6f',
      values: [],
      finger: { index: 0 }
    };
  },
  computed: {
    iconStyle () {
      return 'on-color';
    },
    pinColors () {
      return this.pins
        .map(pin => {
          return pin.color;
        });
    }
  },
  beforeMount () {
    this.values = Array(this.digitsNumber)
      .fill(0);
  },
  methods: {
    isPinOn (index) {
      return this.pins.some((pin) => {
        return pin.index === index;
      });
    },
    tapPin (id) {
      this.pins
        .find(pin => {
          return pin.color === this.selectedPinColor;
        })
        .index = id;
    },
    pinColor (index) {
      const pin = this.pins.find((pin) => {
        return pin.index === index;
      });
      return pin ? pin.color : '';
    },
    selectPinColor (color) {
      this.selectedPinColor = color;
    },
    hasPoint (index) {
      return index % 3 === 2;
    },
    isFingerOn (index) {
      return this.finger.index === index;
    },
    tapFinger (id) {
      this.finger.index = id;
    },
    valueChanged ({ id, value }) {
      this.values[id] = value;
    },
    clear () {
      this.pins.map((pin, index) => {
        pin.index = index;
      });
      this.values.length = 0;
      this.values = Array(this.digitsNumber)
        .fill(0);
      this.finger.index = 0;
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

    /* background: blanchedalmond; */
  }
    .soroban__rod {
      margin: 0 3px;
    }
    .soroban__tool {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      margin-left: 24px;
      position: relative;

      /* background: black; */
      width: 80px;  height: 168px;
    }
      .soroban__pin-selector {
        position: absolute;
        top: 0;

        /* background: black; */
        width: 100%;
      }
      .soroban__clear {
        margin-left: 9px;

        background-color: #ff615033;
        width: 66px; height: 66px;
        border-radius: 50%;
        border: none;

        display: flex;
        align-items: center;
        justify-content: center;

        color: #ff6150;
        font-size: 28px;
      }
</style>

