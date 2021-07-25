<template>
  <div class="column">
    <Rod />
    <div class="column__finger">
      <i class="las la-hand-point-left"></i>
    </div>
  </div>
</template>

<script>
import Rod from "./Rod.vue"

export default {
  components: {
    Rod,
  }
}
</script>

<style scoped>
  @import url("https://maxst.icons8.com/vue-static/landings/line-awesome/line-awesome/1.3.0/css/line-awesome.min.css");
  @import url("https://use.fontawesome.com/releases/v5.6.1/css/all.css");


  .column {}
    .column__finger {
      font-size: 26px;
      margin-left: -4px;
      transform: rotate(90deg);
    }
</style>