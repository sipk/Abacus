<template>
  <div class="problem">
    <input class="problem__formula"
        v-model="formula"
        type="text" 
        placeholder="12+34"
      >
    <div class="problem__tool">
      <button class="problem__clear"
          @click="clear"
        >
        <i class="las la-backspace"
            :class="iconStyle"
          >
        </i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      formula: '',
    }
  },
  computed: {
    iconStyle () {
      return 'on-color';
    }
  },
  methods: {
    clear () {
      this.formula = '';
    }
  }
}
</script>

<style scoped>
  .on-color {
    color: #ff6150;
    opacity: 1;
  }

  .problem {
    display: flex;
    align-items: center;
    justify-content: center;
  }
    .problem__formula {
      color: #134e6f;
      font-size: 60px;
      width: 100%;

      text-align: center;
    }
    .problem__tool {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      margin-left: 24px;
      position: relative;

      /* background: black; */
      width: 80px;  height: 160px;
    }
      .problem__clear {
        background-color: #ff615033;
        font-size: 32px;
        width: 66px; height: 66px;
        border-radius: 50%;
        border: none;

        display: flex;
        align-items: center;
        justify-content: center;

        cursor: pointer;
      }
</style>