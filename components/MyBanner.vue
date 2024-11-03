<script lang="ts" setup>
import anime from "animejs";
import gsap from "gsap";
const banner = ref<HTMLElement | null>();
const text = ref();
const splittext = (element) => {
  let newElement = element.value.innerText.split("").map((char, index) => {
    if (char === " ") return `<br>`;
    return `<span class="letter">${char}</span>`;
  });
  element.value.innerHTML = newElement.join("");
};
onMounted(() => {
  //init state
  splittext(text);
  gsap.set(".banner .letter", { translateY: "300px", rotate: 180 });
  gsap.to(".banner", { opacity: 1, delay: 1.5 });

  anime({
    targets: ".border rect",
    strokeDashoffset: [anime.setDashoffset, 0],
    easing: "easeInOutSine",
    duration: 1500,
    delay: function (el, i) {
      return i * 250 + 1500;
    },
    complete: function () {
      banner.value?.classList.add("active");
    },
  });

  gsap.to(".banner .letter", {
    translateY: 0,
    rotate: 0,
    stagger: 0.03,
    duration: 0.75,
    ease: "elastic.out(1,0.75)",
    delay: 3.5,
  });

  gsap.to(".banner p", {
    color: "#0e7700",
    duration: 0.5,
    ease: "elastic.out(1,0.75)",
    delay: 4.6,
  });

  anime({
    targets: ".border::after",
    top: "0",
    easing: "easeInOutSine",
    duration: 1500,
    delay: 3000,
    onComplete: function () {
      banner.value?.classList.add("active");
    },
  });
});
</script>

<template>
  <div class="banner" ref="banner">
    <svg
      width="60"
      height="300"
      viewBox="0 0 60 300"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      class="border"
    >
      <rect
        x="1"
        y="1"
        width="58"
        height="298"
        rx="29"
        stroke="black"
        stroke-width="2"
      />
    </svg>
    <p ref="text">東京の幽霊・</p>
  </div>
</template>

<style lang="scss" scoped>
.banner {
  opacity: 0;
  width: 60px;
  height: 300px;
  top: 35%;
  right: 20px;
  position: absolute;
  border-radius: 40px;
  overflow: hidden;
  &::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #d12f2d;
    transition: top 0.5s ease;
    transition-delay: 0.2s;
    top: 100%;
  }
  &::before {
    content: "";
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    height: 100%;
    background: #cbf7d1;
    transition: top 0.5s ease;
    transition-delay: 1.5s;
    z-index: 1;
  }
  rect {
    transition: stroke 0.5s ease;
    transition-delay: 1.5s;
  }
  &.active {
    rect {
      stroke: #0e7700;
    }
    &::after {
      top: 0;
    }
    &::before {
      top: 0;
    }
  }

  svg {
    position: absolute;
    top: 0;
    right: 0;
    z-index: 1;
  }
  p {
    color: #fff;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    z-index: 2;
    font-weight: 900;
    font-size: rem(36);
    line-height: 1.2;
    text-align: center;
    margin-top: rem(20);
  }
}
</style>
