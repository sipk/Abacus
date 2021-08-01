<template>
  <div class="main">
    <div class="main__problem">
      <div class="main__title">PROBLEM</div>
      <Problem class="main__content" />
    </div>
    <div class="main__soroban-view">
      <div class="main__title">SOROBAN</div>
      <SorobanView class="main__content" />
    </div>
    <div class="main__drawing">
      <div class="main__title">DRAWING</div>
      <Drawing class="main__content" />
    </div>
  </div>
</template>

<script>
import Problem from './Problem.vue'
import SorobanView from './SorobanView.vue'
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
      padding: 20px;
      border-radius: 3px;

      display: flex;
      align-items: center;
      justify-content: center;

      position: relative;
    }
    .main__problem {
      height: 180px;
    }
    .main__soroban-view,
    .main__drawing {
      height: 300px;
    }
      .main__title {
        font-size: 13px;
        position: absolute;
        top: 28px;  left: 18px;

        position: absolute;
      }
      .main__content {
        /* background-color: teal; */
        width: 80%;
      }
</style>