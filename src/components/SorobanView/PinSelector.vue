<template>
  <div class="pin-selector">
    <div class="pin-selector__item"
        v-for="(option, i) in options"
        :key="i"
      >
      <input 
          type="radio"
          name="group"
          :id="option"
          :value="option"
          v-model="innerSelected"
        />
      <label 
          class="pin-selector__color"
          :style="colorStyle(option)"
          :for="option"
        >
      </label>
    </div>
  </div>
</template>

<script>
export default ({
  props: {
    options: Array,
    selected: String
  },
  computed: {
    innerSelected: {
      get () {
        return this.$props.selected;
      },
      set (value) {
        this.$emit('valueChanged', value);
      }
    }
  },
  methods: {
    colorStyle (color) {
      return {
        backgroundColor: color
      }
    }
  }
})
</script>

<style scoped>
  .pin-selector {
    display: flex;
    justify-content: space-between;
    
    /* background-color: olivedrab; */
    width: 100%;  height: 26px;
  }
    .pin-selector__item {
      position: relative;
    }
    .pin-selector__item:hover input ~ .pin-selector__color {
      /* background: #d8a22e; */
    }
      .pin-selector__color {
        position: absolute;
        left: 0;  top: 0;

        /* background-color: #134e6f; */
        width: 26px;  height: 26px;
        border-radius: 50%;

        cursor: pointer;
      }
      .pin-selector__color::after {
        display: none;
        position: absolute;
        left: 5px;  top: 1px;

        font-family: "Line Awesome Free";
        content: "\f00c";
        color: #fff;
      }
      input {
        opacity: 0;
      }
      input:checked ~ .pin-selector__color::after {
        display: block;
        opacity: 1;
      }
</style>