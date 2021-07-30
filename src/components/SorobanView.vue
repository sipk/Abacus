<template>
  <div class="soroban-view">
    <Pin class="soroban-view__pin" />
    <Soroban class="soroban-view__soroban" />
    <Finger class="soroban-view__finger" />
  </div>
</template>

<script>
import Soroban from './SorobanView/Soroban/Soroban.vue'
import Pin from './SorobanView/Marker/Pin.vue'
import Finger from './SorobanView/Marker/Finger.vue'

export default {
  components: {
    Soroban,
    Pin,
    Finger,
  },
}
</script>

<style scoped>
  .soroban-view {}
    .soroban-view__pin {}

    .soroban-view__soroban {
      /* background-color:teal; */
    }
    
    .soroban-view__finger {
      /* background-color: thistle; */
      margin-top: -15px;
    }
</style>