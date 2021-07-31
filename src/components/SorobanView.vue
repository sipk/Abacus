<template>
  <div class="view">
    <Soroban class="view__soroban" />
  </div>
</template>

<script>
import Soroban from './SorobanView/Soroban.vue'

export default {
  components: {
    Soroban
  },
}
</script>

<style scoped>
  .view {}
    .view__soroban {}
</style>