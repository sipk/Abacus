<template>
  <div class="rod">
    <div class="rod__upper">
      <div class="rod__5bead"
          :style="fiveBeadStyle"
          @click="repel5Bead"
        >
      </div>
    </div>
    <div class="rod__bar">
      <div class="rod__point"
          v-if="hasPoint"
        >
      </div>
    </div>
    <div class="rod__lower">
      <div class="rod__1bead"
          v-for="(isOn, index) in is1BeadOn"
          :key="index"
          :style="oneBeadStyles[index]"
          @click="repel1Bead(index)"
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    hasPoint: Boolean,
    value: Number,
    beadColor: String
  },
  computed: {
    is5BeadOn () {
      return this.value >= 5;
    },
    is1BeadOn () {
      const isOn = [];
      const lowerNo = this.value % 5;
      for (let i = 0; i < 4; i++) {
        isOn.push(i < lowerNo);
      }
      return isOn;
    },
    fiveBeadStyle () {
      return {
        "--borderRightColor": this.beadColor,
        "--borderLeftColor": this.beadColor,
        backgroundColor: this.beadColor,
        transform: this.is5BeadOn 
          ? 'translateY(14px)'
          : 'translateY(0)'
      }
    },
    oneBeadStyles () {
      return this.is1BeadOn
        .map(isOn => {
          return {
            "--borderRightColor": this.beadColor,
            "--borderLeftColor": this.beadColor,
            backgroundColor: this.beadColor,
            transform: isOn
              ? 'translateY(0)'
              : 'translateY(14px)'
          }
        })
    }
  },
  methods: {
    repel5Bead () {
      const value = this.is5BeadOn
        ? this.value - 5
        : this.value + 5;
      this.$emit('valueChanged', value);
    },
    repel1Bead (index) {
      const upperValue = this.is5BeadOn ? 5 : 0;
      const value = this.is1BeadOn[index]
        ? upperValue + index
        : upperValue + index + 1;
      this.$emit('valueChanged', value);
    },
  }
}
</script>

<style scoped>
.rod {}
  .rod__upper {
    /* background-color: cadetblue; */
    height: 28px;

    display: flex;
    justify-content: center;
  }
  .rod__bar {
    /* background-color: #222; */
    height: 12px;
    /* border-radius: 40%; */

    display: flex;
    align-items: center;
    justify-content: center;
  }
    .rod__point {
      background-color: #ff6150;
      width: 5px; height: 5px;
      border-radius: 50%;
    }
  .rod__lower {
    /* background-color: cadetblue; */
    height: 70px;

    display: flex;
    flex-direction: column;
    align-items: center;
  }

  /* .rod__5bead,
  .rod__1bead {
    height: 14px; width: 22px;
    border-radius: 50%;

    transition: background-color .4s ease;
    transition: transform .4s ease;

    cursor: pointer;
  } */

  .rod__5bead,
  .rod__1bead {
    position: relative;
    
    height: 14px; width: 7px;
    --borderRightColor: var(--beadColor);
    --borderLeftColor: var(--beadColor);

    transition: background-color .4s ease, transform .4s ease;

    cursor: pointer;
  }
  .rod__5bead::before,
  .rod__5bead::after,
  .rod__1bead::before,
  .rod__1bead::after {
    position: absolute;
    top: 0;

    content: '';
    height: 0;  width: 0;
    border: 7px solid transparent;
    border-right: 8px solid transparent;
    border-left: 8px solid transparent;
  }
  .rod__5bead::before,
  .rod__1bead::before {
    right: 100%;
    border-right-color: var(--borderRightColor);
  }
  .rod__5bead::after,
  .rod__1bead::after {
    left: 100%;
    border-left-color: var(--borderLeftColor);
  }
</style>