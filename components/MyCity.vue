<script lang="ts" setup></script>

<template>
  <div class="img">
    <img src="/tokyo.png" alt="" />
    <div class="fog"></div>
    <div class="fog2"></div>
  </div>
</template>

<style lang="scss" scoped>
.img {
  position: relative;
  width: 100%;
  height: auto;
  overflow: hidden;
  > img {
    width: 100%;
    height: auto;
  }
  .fog,
  .fog2 {
    position: absolute;
    left: 0;
    top: 0;
    width: 250%;
    height: 100%;
    overflow: hidden;
    background-image: url("/fog.png");
    background-size: 100% 150px;
    background-position: bottom;
    background-repeat: repeat-x;
    opacity: 0.5;
    animation: fog 80s linear infinite;
  }
  @keyframes fog {
    0% {
      transform: translateX(-60%);
    }
    100% {
      transform: translateX(60%);
    }
  }
  @keyframes fog2 {
    0% {
      transform: translateX(0%);
    }
    100% {
      transform: translateX(-30%);
    }
  }
  .fog2 {
    height: 50%;
    top: 20%;
    opacity: 0.3;
    background-size: 100% 100px;
    background-image: url("/fog2.png");
    animation: fog2 100s linear infinite;
  }
}
</style>
