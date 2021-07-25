<template>
  <div class="main">
    <h1 class="main__title">Soroban</h1>
    <SorobanView class="main__soroban-view" />
  </div>
</template>

<script>
import SorobanView from './SorobanView/SorobanView.vue'

export default {
  components: {
    SorobanView,
  },
}
</script>

<style scoped>
  .main {
    /* background-color: steelblue; */
    height: 50vh;
  }
    .main__title {}

    .main__soroban-view {}
</style>