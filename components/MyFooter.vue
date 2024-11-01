<script lang="ts" setup>
import anime from "animejs";

const state1 = [20, 80, 60, 20, 40, 60];
// fait une state 2 ou les valeurs gardent le meme total mais les valeurs sont differentes
const state2 = [70, 60, 20, 20, 50, 60];
const state3 = [60, 20, 40, 40, 60, 20];
onMounted(() => {
  let selected = 1;
  let timing = 1500;

  const animation = (selectedState: number[], nextState: number) => {
    for (let i = 0; i < 6; i++) {
      anime({
        targets: `.footer__main-deco${i + 1}`,
        width: `${selectedState[i]}px`,
        duration: timing,
        easing: 'easeInBounce',
      });
    }
    setTimeout(() => {
      selected = nextState;
      animationSwitch();
    }, timing);
  };
  let animationSwitch = () => {
    switch (selected) {
      case 1:
        animation(state1, 2);
        break;
      case 2:
        animation(state2, 3);

        break;
      case 3:
        animation(state3, 1);

        break;

      default:
        break;
    }
  };
  animationSwitch();
});
</script>

<template>
  <footer class="footer">
    <div class="footer__item footer__me">
      dev by
      <NuxtLink to="https://www.heinis.dev" external>Quentin Heinis</NuxtLink>
    </div>
    <div class="footer__item footer__main">
      Tokyo - Japan
      <div class="flex">
        <span class="footer__main-deco1" />
        <span class="footer__main-deco2" />
        <span class="footer__main-deco3" />
        <span class="footer__main-deco4" />
        <span class="footer__main-deco5" />
        <span class="footer__main-deco6" />
      </div>
    </div>
    <div class="footer__item footer__date">
      <div class="flex">
        <span></span>
        <span></span>
      </div>
      01-11-2024
    </div>
  </footer>
</template>

<style lang="scss" scoped>
.footer {
  height: 100px;
  background-color: #d12f2d;
  display: flex;
  justify-content: space-between;
  padding-inline: rem(24);
  color: #fff;
  &__item {
    width: 100%;
  }
  &__me {
    display: flex;
    justify-content: flex-end;
    flex-direction: column;
    a {
      color: inherit;
      text-decoration: none;
    }
  }
  .flex {
    display: flex;
    gap: 10px;
  }
  &__date {
    display: flex;
    justify-content: flex-end;
    flex-direction: column;
    align-items: flex-end;

    span {
      height: rem(40);
      width: rem(40);
      display: block;
      background: red;
    }
  }
  &__main {
    display: flex;
    flex-direction: column;
    align-items: center;
    font-size: rem(36);
    text-transform: uppercase;
    font-weight: 900;
    span {
      height: rem(10);
      border-radius: 20px;
      display: block;
      border: 1px solid #fff;
      &:nth-child(1) {
        width: rem(20);
      }
      &:nth-child(2) {
        width: rem(80);
      }
      &:nth-child(3) {
        width: rem(60);
      }
      &:nth-child(4) {
        width: rem(20);
      }
      &:nth-child(5) {
        width: rem(40);
      }
      &:nth-child(6) {
        width: rem(60);
      }
    }
  }
}
</style>
