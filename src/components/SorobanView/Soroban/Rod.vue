<template>
  <div class="rod">
    <Bead class="rod__5bead"
        :value="isFiveBeadOn"
        :id="5"
        @input="repelFive" 
      />
    <div class="rod__space"></div>
    <Bead class="rod__1bead"
        v-for="(isOn, idx) in isOneBeadOn"
        :key="idx"
        :value="isOn"
        :id="idx"
        @input="repelOne" 
      />
  </div>
</template>

<script>
import Bead from "./Bead.vue";

export default {
  components: {
    Bead,
  },
  data () {
    return {
      oneBeadNumber: 4,
      isFiveBeadOn: false,
      isOneBeadOn: [],
    };
  },
  beforeMount () {
    this.isFiveBeadOn = false;
    this.isOneBeadOn = Array(this.oneBeadNumber)
      .fill(true);
  },
  methods: {
    repelFive ({ value }) {
      this.isFiveBeadOn = value;
    },
    repelOne ({ value, id }) {
      this.isOneBeadOn.length = 0;
      for (let i = 0; i < this.oneBeadNumber; i++) {
        const isOn = (i === id)
          ? value 
          : i > id;
        this.isOneBeadOn.push(isOn);
      }
    }
  }
};
</script>

<style scoped>
  .rod {
    /* background-color: steelblue; */
    height: 101px;  width: 22px;
    /* display: block; */
    position: relative;
  }
    .rod__5bead {}
    .rod__1bead {
      position: absolute;
    }
    .rod__1bead:nth-of-type(3) {
      TOP: 31px;
    }
    .rod__1bead:nth-of-type(4) {
      TOP: 45px;
    }
    .rod__1bead:nth-of-type(5) {
      TOP: 59px;
    }
    .rod__1bead:nth-of-type(6) {
      TOP: 73px;
    }
    .rod__space {
      /* display: block; */
      background-color: #666666;
      height: 3px;  width: 100%;
    }
</style>

