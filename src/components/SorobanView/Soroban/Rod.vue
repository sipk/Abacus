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
    hasPoint: Boolean
  },
  data () {
    return {
      value: 0,
    }
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
        transform: this.is5BeadOn 
          ? 'translateY(14px)'
          : 'translateY(0)'
      }
    },
    oneBeadStyles () {
      return this.is1BeadOn
        .map(isOn => {
          return {
            transform: isOn
              ? 'translateY(0)'
              : 'translateY(14px)'
          }
        })
    }
  },
  methods: {
    repel5Bead () {
      this.value = this.is5BeadOn
        ? this.value - 5
        : this.value + 5;
    },
    repel1Bead (index) {
      const upperValue = this.is5BeadOn ? 5 : 0;
      this.value = this.is1BeadOn[index]
        ? upperValue + index
        : upperValue + index + 1;
    },
  }
}
</script>

<style scoped>
.rod {}
  .rod__upper {
    /* background-color: cadetblue; */
    height: 28px;
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
      background-color: #222;
      width: 5px; height: 5px;
      border-radius: 50%;
    }
  .rod__lower {
    /* background-color: cadetblue; */
    height: 70px;
  }

  .rod__5bead,
  .rod__1bead {
    background-color: #222;
    height: 14px; width: 22px;
    border-radius: 50%;

    transition: transform .4s ease;

    cursor: pointer;
  }
</style>