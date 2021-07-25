<template>
  <div>
    <div class="bead"
      >
      <div class="bead__item"
          :style="indicatorStyles" 
        role="checkbox"
        @click="toggle"
        />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Boolean,
      required: true
    },
    id: Number
  },
  computed: {
    backgroundStyles () {
      return;
      return {
        'gold-mid': this.value,
        'gray-lighter': !this.value
      };
    },
    indicatorStyles () {
      return {
        transform: this.value
          ? 'translateY(14px)' 
          : 'translateY(0)'
      };
    }
  },
  methods: {
    toggle () {
      this.$emit('input', { value: !this.value, id: this.id });
    }
  }
}
</script>

<style scoped>
  .bead {
    /* background-color: #cccccc; */
    height: 28px; width: 22px;

    /* pointer-events: none; */
  }
    .bead__item {
      background-color: #666666;
      height: 14px; width: 22px;
      border-radius: 50%;

      transition: transform .4s ease;

      cursor: pointer;
    }
</style>