<script lang="ts" setup>
import gsap from "gsap";
const svg = ref();
const animateCircle = () => {
  let circle1 = [
    {
      borderWidth: "40px",
      size: "75%",
    },
    {
      borderWidth: "0px",
      size: "90%",
    },
    {
      borderWidth: "8px",
      size: "95%",
    },
    {
      borderWidth: "8px",
      size: "0%",
    },
    {
      borderWidth: "25px",
      size: "75%",
    },
  ];

  let circle2 = [
    {
      borderWidth: "20px",
      size: "60%",
    },
    {
      borderWidth: "5px",
      size: "80%",
    },
    {
      borderWidth: "2px",
      size: "0%",
    },
  ];

  gsap.to(".circles__effect.-e1", {
    "--effectsize": circle1[0].size,
    "--borderwidth": circle1[0].borderWidth,
    duration: 0.55,
  });
  gsap.to(".circles__effect.-e1", {
    "--effectsize": circle1[1].size,
    "--borderwidth": circle1[1].borderWidth,
    duration: 0.5,
    delay: 0.55,
  });
  gsap.to(".circles__effect.-e2", {
    "--effectsize2": circle2[0].size,
    "--borderwidth2": circle2[0].borderWidth,
    duration: 0.5,
    delay: 0.55,
  });
  gsap.to(".circles__effect.-e2", {
    "--effectsize2": circle2[1].size,
    "--borderwidth2": circle2[1].borderWidth,
    duration: 0.5,
    delay: 1,
  });
  gsap.to(".circles__effect.-e2", {
    "--effectsize2": circle2[2].size,
    "--borderwidth2": circle2[2].borderWidth,
    duration: 0.5,
    delay: 1.6,
  });
  gsap.to(".circles__effect.-e1", {
    "--effectsize": circle1[2].size,
    "--borderwidth": circle1[2].borderWidth,
    duration: 0.1,
    delay: 1.5,
  });
  gsap.to(".circles__effect.-e1", {
    "--effectsize": circle1[3].size,
    "--borderwidth": circle1[3].borderWidth,
    duration: 1,
    delay: 1.6,
  });
  gsap.to(".circles__effect.-e1", {
    "--effectsize": circle1[4].size,
    "--borderwidth": circle1[4].borderWidth,
    duration: 1,
    delay: 2.6,
  });
};
const generateRectangles = () => {
  let svgWidth = svg.value.getBoundingClientRect().width;
  let svgHeight = svg.value.getBoundingClientRect().height;
  let rectWidth = 20;
  let rectHeight = 20;
  let rows = svgHeight / rectHeight;
  let columns = svgWidth / rectWidth;
  let rects = [];
  for (let i = 0; i < rows; i++) {
    for (let j = 0; j < columns; j++) {
      rects.push(
        `<rect class="reveal" x="${j * rectWidth}" y="${
          i * rectHeight
        }" width="${rectWidth}" height="${rectHeight}" fill="white" />`
      );
    }
  }
  svg.value.innerHTML = rects.join("");
};
const revealMountains = () => {
  generateRectangles();
  gsap.set(".city", { opacity: 1 });

  gsap.to(".reveal", {
    opacity: 0,
    duration: 0.075,
    stagger: { amount: 1, from: "random", axis: "x" },
    delay: 1,
  });
};
onMounted(() => {
  revealMountains();
  gsap.to("svg .reveal", {
    opacity: 0,
    delay: 2,
  });

  setTimeout(() => {
    gsap.to(".circles__main", {
      translateX: "-50%",
      duration: 0,
    });
    gsap.to(".circles__main", {
      scale: 1,
    });
  }, 2000);
  setTimeout(() => {
    animateCircle();
  }, 2300);

  // animateCircle();
});
</script>

<template>
  <div class="city">
    <div class="circles">
      <span class="circles__main" />
      <span class="circles__effect -e1" />
      <span class="circles__effect -e2" />
    </div>
    <div class="img">
      <img src="/tokyo.png" alt="" />
      <div class="fog"></div>
      <div class="fog2"></div>
      <svg
        width="100%"
        height="100%"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
        ref="svg"
      ></svg>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.city {
  position: relative;
  z-index: 0;
  opacity: 0;

}
.circles {
  --size: 250px;
  &__main {
    width: var(--size);
    height: var(--size);

    background-color: #d12f2d;
    border-radius: 50%;
    position: absolute;
    top: 10%;
    left: 50%;
    transform: translateX(-50%);

    scale: 0;
  }
  &__effect {
    width: var(--size);
    height: var(--size);
    border-radius: 50%;
    position: absolute;
    top: 10%;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    justify-content: center;
    align-items: center;
    &::after {
      content: "";
      width: 75%;
      height: 75%;
      border: 20px solid #fff;
      border-radius: 50%;
    }
    &.-e1 {
      --effectsize: 0%;
      --borderwidth: 8px;
      &::after {
        width: var(--effectsize);
        height: var(--effectsize);
        border-width: var(--borderwidth);
      }
    }
    &.-e2 {
      --effectsize2: 0%;
      --borderwidth2: 8px;
      &::after {
        width: var(--effectsize2);
        height: var(--effectsize2);
        border-width: var(--borderwidth2);
      }
    }
  }
}
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
  svg {
    /*   width: 100%;
  height: 100%; */
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
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
