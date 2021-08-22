<template>
  <div class="switch">
    <label
        class="switch__item"
        for="switch"
      >
      <input
          type="checkbox" 
          id="switch"
          v-model="innerSelected"
        />
      <div class="switch__label">1-100</div>
      <div 
          class="switch__background"
          :style="backgroundStyle"
        >
      </div>
      <div 
          class="switch__indicator"
          :style="indicatorStyle"
        >
      </div>
    </label>
  </div>
</template>

<script>
export default ({
  props: {
    selected: Boolean
  },
  computed: {
    innerSelected: {
      get () {
        return this.$props.selected;
      },
      set (isSelected) {
        this.$emit('valueChanged', isSelected);
      }
    },
    backgroundStyle () {
      return { 
        backgroundColor: this.selected 
          ? "#134e6f66" 
          : "#bec0c6" 
      };
    },
    indicatorStyle () {
      return { 
        backgroundColor: this.selected 
          ? "#134e6f" 
          : "#fff",
        transform: this.selected 
          ? 'translateX(0)' 
          : 'translateX(-12px)' 
      };
    }
  }
})
</script>


<style scoped>
  .switch {
    /* background-color: blueviolet; */
    width: 100%;
  }
    .switch__item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      position: relative;
    }
    .switch__label {
      font-size: 18px;
      color: #555;
    }
    .switch__background {
      position: absolute;
      right: 0;

      /* background-color: #bec0c6; */
      /* background-color: #134e6f66; */
      width: 36px;  height:16px;
      border-radius: 10px;

      transition: background-color .4s ease;
    }
    .switch__indicator {
      position: absolute;
      right: 0;

      /* background-color: #eef0f6; */
      /* background-color: #134e6f; */
      width: 24px; height: 24px;
      border-radius: 50%;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);

      transition: transform .4s ease;

      cursor: pointer;
    }
    input {
      display: none;
      opacity: 0;
    }
    input:checked ~ .switch__indicator {
      display: block;
      opacity: 1;
    }
</style>