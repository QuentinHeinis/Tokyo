<script lang="ts" setup>
import gsap from "gsap";
import anime from "animejs/lib/anime.es.js";

onMounted(() => {
  // init state

  gsap.set(".tokyo #t .first", { scaleX: 0 });
  gsap.set(".tokyo #t .second", { scaleY: 0 });
  gsap.set(".tokyo #t .third", { scaleX: 0 });
  gsap.set(".tokyo #k .first", { scaleX: 0 });
  gsap.set(".tokyo #k .second", { scaleY: 0 });
  gsap.set(".tokyo #y .first", { translateX: 50, opacity: 0 });
  gsap.set(".tokyo #y .second", { opacity: 0 });

  gsap.set(".tokyo #o2", { scale: 0, transformOrigin: "50% 50%" });


  gsap.set(".tokyo", { opacity: 1 });
  // animate the first o
  anime({
    targets: ".tokyo .o",
    d: [
      {
        value:
          "M111.5 9.06723V121H217.5V9.06723H170.052V1H157.938V9.06723H111.5ZM148.796 45.5H181.676V84H148.796V45.5Z",
      },
      {
        value:
          "M55.5 9.06723V121H273.5V9.06723H170.052V1H157.938V9.06723H55.5ZM92.7963 45.5H237.676V84H92.7963V45.5Z",
      },
      {
        value:
          "M111.5 9.06723V121H217.5V9.06723H170.052V1H157.938V9.06723H111.5ZM148.796 45.5H181.676V84H148.796V45.5Z",
      },
    ],
    duration: 2000,
    easing: "easeInOutQuad",
  });

  // animate the t
  gsap.to(".tokyo #t .first", {
    scaleX: 1,
    duration: 0.5,
    delay: 1.5,
    ease: "power1.inOut(1.7)",
  });
  gsap.to(".tokyo #t .second", {
    scaleY: 1,
    duration: 0.5,
    delay: 1.7,
    ease: "power1.inOut(1.7)",
  });
  gsap.to(".tokyo #t .third", {
    scaleX: 1,
    duration: 0.5,
    delay: 1.9,
    ease: "power1.inOut(1.7)",
  });

  // animate the k
  gsap.to(".tokyo #k .first", {
    scaleX: 1,
    duration: 0.5,
    delay: 2.1,
    ease: "power1.inOut(1.7)",
  });
  gsap.to(".tokyo #k .second", {
    scaleY: 1,
    duration: 0.5,
    delay: 2.3,
    ease: "power1.inOut(1.7)",
  });

  // animate the y
  gsap.to(".tokyo #y .first", {
    translateX: 0,
    opacity: 1,
    duration: 0.5,
    delay: 2.5,
    ease: "power1.inOut(1.7)",
  });
  gsap.to(".tokyo #y .second", {
    opacity: 1,
    duration: 0.5,
    delay: 2.7,
    ease: "power1.inOut(1.7)",
  });

  // animate the second o
  gsap.to(".tokyo #o2", {
    scale: 1,
    duration: 0.5,
    delay: 3,
    ease: "elastic.out(1, 0.4)",
  });


});
</script>

<template>
  <header class="tokyo-wrapper">
    <svg
      width="535"
      height="131"
      viewBox="0 0 535 131"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      class="tokyo"
    >
      <path
        fill-rule="evenodd"
        clip-rule="evenodd"
        d="M111.5 9.06723V121H217.5V9.06723H170.052V1H157.938V9.06723H111.5ZM148.796 45.5H181.676V84H148.796V45.5Z"
        fill="#d12f2d"
        class="o"
      />

      <g id="o2">
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M429.5 9.06723V121H535.5V9.06723H488.052V1H475.938V9.06723H429.5ZM466.796 45.5H499.676V84H466.796V45.5Z"
          fill="#d12f2d"
          stroke="#d12f2d"
        />
      </g>
      <g id="y">
        <path
          d="M360 9.5H322V90H360V81H388.5V93.5H322V121.5H345H424.5L426.5 119V9.5H388.5V35.5V61.5H360V35.5V9.5Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="first"
        />
        <path
          d="M370.5 35.5L360 9.5V35.5H370.5Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="second"
        />
        <path
          d="M378 35.5H388.5V9.5L378 35.5Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="second"
        />
        <path
          d="M345 129.5V121.5H322L345 129.5Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="second"
        />
      </g>
      <g id="k">
        <path
          d="M264.5 9.5H220.5V121H264.5V45.5H307H314C316.4 45.5 317.667 43.5 318 42.5V9.5H275.5V26.5H264.5V9.5Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="first"
        />
        <path
          d="M264.5 61C264.5 83.8 277.167 110.5 283.5 121H323V110C308.2 83.2 306.167 55.8333 307 45.5H305L264.5 61Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="second"
        />
      </g>
      <g id="t">
        <path
          d="M109 9H1V45H32H68H109V9Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="first"
        />
        <path
          d="M32 125L34 120L46.5 93L68 45H32C32 45 7.20003 79.7 8.00003 100.5C8.80003 121.3 24.3334 125.5 32 125Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="second"
        />
        <path
          d="M70.5 77L63 93.5L46.5 93L33.5 120.5H76.5C83.7 120.5 94 108.5 94 101V77H70.5Z"
          fill="#d12f2d"
          stroke="#d12f2d"
          class="third"
        />
      </g>
    </svg>
  </header>
</template>

<style lang="scss" scoped>
.tokyo-wrapper {
  display: block;
  position: relative;
}
.tokyo {
  width: 100%;
  height: auto;
  overflow: hidden;
  opacity: 0;
}
</style>
