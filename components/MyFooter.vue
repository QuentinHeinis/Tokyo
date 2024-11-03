<script lang="ts" setup>
import anime from "animejs";
import gsap from "gsap";
const text = ref();

const resizeTiles = () => {
  const state1 = [20, 40, 30, 30, 50, 60];
  const state2 = [30, 60, 30, 20, 40, 50];
  const state3 = [90, 20, 30, 40, 20, 30];

  let selected = 2;
  let timing = 1500;
  let delay = 250;

  const animation = (selectedState: number[], nextState: number) => {
    for (let i = 0; i < 6; i++) {
      anime({
        targets: `.footer__main-deco${i + 1}`,
        width: `${selectedState[i]}px`,
        duration: timing,
        easing: "easeOutBounce",
      });
    }
    setTimeout(() => {
      selected = nextState;
      animationSwitch();
    }, timing + delay);
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
};
const squareToCircle = () => {
  anime({
    targets: ".squareCircle",
    borderRadius: ["10px", "50%"],
    duration: 750,
    loop: true,
    endDelay: 500,
    delay: 500,
    direction: "alternate",
  });
  anime({
    targets: ".lines .l1",
    translateX: ["-2px", "2px"],
    translateY: ["-2px", "2px"],
    duration: 750,
    loop: true,
    endDelay: 500,
    delay: 500,
    direction: "alternate",
  });
  anime({
    targets: ".lines .l2",
    translateX: ["2px", "-2px"],
    translateY: ["-2px", "2px"],
    duration: 750,
    loop: true,
    endDelay: 500,
    delay: 500,
    direction: "alternate",
  });
  anime({
    targets: ".lines .l3",
    translateX: ["2px", "-2px"],
    translateY: ["2px", "-2px"],
    duration: 750,
    loop: true,
    endDelay: 500,
    delay: 500,
    direction: "alternate",
  });
  anime({
    targets: ".lines .l4",
    translateX: ["-2px", "2px"],
    translateY: ["2px", "-2px"],
    duration: 750,
    loop: true,
    endDelay: 500,
    delay: 500,
    direction: "alternate",
  });
};
const splittext = (element: Ref) => {
  let newElement = element.value.innerText.split("").map((char, index) => {
    if (char === " ") return `<span class="letter">&nbsp;</span>`;
    return `<span class="letter">${char}</span>`;
  });
  element.value.innerHTML = newElement.join("");
};
onMounted(() => {
  //init state
  splittext(text);
  gsap.set(".footer__main p .letter", {
    opacity: 0,
    translateX: function (index) {
      if (index > 7) {
        console.log();
        let x = (index - 6) * 100 - 50;
        return x;
      }
      if (index == 6) return 0;
      let x = (index - 5) * 100 - 50;
      return x;
    },
  });
  gsap.set(".footer__me", { opacity: 0, translateY: 50 });
  gsap.set(".footer__main", { opacity: 0, translateY: 50 });
  gsap.set(".footer__date", { opacity: 0, translateY: 50 });

  //animate state

  gsap.to(".footer .footer__wrapper", {
    height: "100px",
    duration: 0.4,
    delay: 1,
  });

  gsap.to(".footer__main p .letter", {
    opacity: 1,
    translateX: 0,
    duration: 0.75,
    ease: "elastic.out(1,1)",
    delay: 1.5,
  });

  gsap.to(".footer__main", {
    opacity: 1,
    translateY: 0,
    duration: 0.75,
    ease: "elastic.out(1,1)",
    delay: 1.5,
  });

  gsap.to(".footer__me", {
    opacity: 1,
    translateY: 0,
    duration: 0.75,
    ease: "elastic.out(1,1)",
    delay: 1.5,
  });
  gsap.to(".footer__date", {
    opacity: 1,
    translateY: 0,
    duration: 0.75,
    ease: "elastic.out(1,1)",
    delay: 1.5,
  });

  resizeTiles();
  squareToCircle();
});
</script>

<template>
  <footer class="footer">
    <div class="footer__wrapper">
      <div class="footer__item footer__me">
        dev by
        <NuxtLink to="https://www.heinis.dev" target="_blank" external>Quentin Heinis</NuxtLink>
      </div>
      <div class="footer__item footer__main">
        <p ref="text">Tokyo - Japan</p>
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
          <span class="squareCircle">
            <svg
              width="22"
              height="22"
              viewBox="0 0 22 22"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              class="lines"
            >
              <path
                class="l1"
                d="M1 1L11 11"
                stroke="#d12f2d"
                stroke-width="2px"
              />
              <path
                class="l2"
                d="M21 1L11 11"
                stroke="#d12f2d"
                stroke-width="2px"
              />
              <path
                class="l3"
                d="M21 21L11 11"
                stroke="#d12f2d"
                stroke-width="2px"
              />
              <path
                class="l4"
                d="M11 11L1 21"
                stroke="#d12f2d"
                stroke-width="2px"
              />
            </svg>
          </span>
          <span class="squareCircle -s2">
            <svg
              width="22"
              height="22"
              viewBox="0 0 22 22"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
              class="lines"
            >
              <path
                class="l1"
                d="M1 1L11 11"
                stroke="#fff"
                stroke-width="2px"
              />
              <path
                class="l2"
                d="M21 1L11 11"
                stroke="#fff"
                stroke-width="2px"
              />
              <path
                class="l3"
                d="M21 21L11 11"
                stroke="#fff"
                stroke-width="2px"
              />
              <path
                class="l4"
                d="M11 11L1 21"
                stroke="#fff"
                stroke-width="2px"
              />
            </svg>
          </span>
        </div>
        01-11-2024
      </div>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
.footer {
  // opacity: 0;
  height: 100px;
  color: #fff;
  display: flex;
  align-items: flex-end;

  &__wrapper {
    width: 100%;
    display: flex;
    overflow: hidden;
    background-color: #d12f2d;
    padding-inline: rem(24);
    justify-content: space-between;
    height: 0px;
  }
  &__item {
    width: 100%;
  }
  &__me {
    display: flex;
    justify-content: center;
    flex-direction: column;
    font-weight: 700;
    text-transform: uppercase;
    line-height: 1;
    font-size: rem(12);
    a {
      font-weight: 400;
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
    justify-content: center;
    flex-direction: column;
    align-items: flex-end;
    line-height: 1;
    font-size: rem(12);
    .squareCircle {
      margin-bottom: rem(8);
      height: rem(40);
      width: rem(40);
      display: block;
      background: white;
      border-radius: 10px;
      position: relative;
      .lines {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
      }
      &.-s2 {
        background: transparent;
        border: 2px solid #fff;
      }
    }
  }
  &__main {
    width: 120%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: rem(36);
    word-break: none;
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
        width: rem(40);
      }
      &:nth-child(3) {
        width: rem(30);
      }
      &:nth-child(4) {
        width: rem(30);
      }
      &:nth-child(5) {
        width: rem(50);
      }
      &:nth-child(6) {
        width: rem(60);
      }
    }
    p {
      // opacity: 0;
      display: flex;
      span {
        display: block;
        width: fit-content;
      }
    }
  }
}
</style>
