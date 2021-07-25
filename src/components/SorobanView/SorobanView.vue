<template>
  <div class="soroban-view">
    <div class="soroban-view__container">
      <Pin class="soroban-view__pin" />
      <Soroban class="soroban-view__soroban" />
      <Finger class="soroban-view__finger" />
    </div>
  </div>
</template>

<script>
import Soroban from './Soroban/Soroban.vue'
import Pin from './Marker/Pin.vue'
import Finger from './Marker/Finger.vue'

export default {
  components: {
    Soroban,
    Pin,
    Finger,
  },
}
</script>

<style scoped>
  .soroban-view {
    /* background-color: tan; */
    height: 50vh;
    /* text-align: center; */

    display: flex;
    align-items: center;
    justify-content: center;

    /* position: relative; */
  }
    .soroban-view__container {}
      .soroban-view__pin {}

      .soroban-view__soroban {
        /* background-color:teal; */
      }
      
      .soroban-view__finger {
        /* background-color: thistle; */
        margin-top: -15px;
      }
</style>