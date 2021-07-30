<template>
  <div class="problem">
    <div class="problem__title">PROBLEM</div>
    <input class="problem__formula"
        type="text" 
        placeholder="32+48"
      >
  </div>
</template>

<style scoped>
  .problem {
    height: 180px;
    padding: 20px;

    display: flex;
    align-items: center;
    justify-content: center;

    position: relative;
  }
    .problem__title {
      font-size: 13px;
      position: absolute;
      top: 28px;  left: 18px;
    }
    .problem__formula {
      color: #134e6f;
      font-size: 60px;
      text-align: center;
    }
</style>