<script lang="ts" setup>
import anime from "animejs";
const banner = ref<HTMLElement | null>();
onMounted(() => {
  anime({
    targets: ".border rect",
    strokeDashoffset: [anime.setDashoffset, 0],
    easing: "easeInOutSine",
    duration: 1500,
    delay: function (el, i) {
      return i * 250;
    },
    complete: function () {
      banner.value?.classList.add("active");
    },
  });
  anime({
    targets: ".border::after",
    top: "0",
    easing: "easeInOutSine",
    duration: 1500,
    delay: 1500,
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
  </div>
</template>

<style lang="scss" scoped>
.banner {
  width: 60px;
  height: 300px;
  top: 40%;
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
}
</style>
