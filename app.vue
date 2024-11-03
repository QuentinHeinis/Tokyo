<template>
  <div class="wrapper">
    <Tokyo />
    <div class="myText">
      <MyTitle />
      <MySubTitle />
      <MyText />
    </div>
    <MyCity />
    <MyFooter />
    <MyBanner />
  </div>
</template>
<style lang="scss">
.wrapper {
  max-width: 800px;
  margin: 0 auto;
  overflow: hidden;
  position: relative;
  .myText {
    position: absolute;
    width: 100%;
  }
}
</style>
