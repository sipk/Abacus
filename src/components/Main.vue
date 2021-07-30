<template>
  <div class="main">
    <Problem class="main__problem" />
    <SorobanView class="main__soroban-view" />
    <Drawing class="main__drawing" />
  </div>
</template>

<script>
import Problem from './Problem.vue'
import SorobanView from './SorobanView/SorobanView.vue'
import Drawing from '../components/Drawing.vue'

export default {
  components: {
    Problem,
    SorobanView,
    Drawing
  },
}
</script>

<style scoped>
  .main {
    height: 100vh;
  }
    .main__problem,
    .main__soroban-view,
    .main__drawing {
      background-color: white;
      /* width: 100vw; height: 300px; */
      margin: 20px 80px;
      border-radius: 3px;
    }
</style>