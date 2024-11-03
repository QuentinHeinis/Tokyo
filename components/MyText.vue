<script lang="ts" setup>
import gsap from "gsap";
let text = ref();
let text2 = ref();
let h3 = ref();
const splittext = (element: Ref) => {
  let newElement = element.value.innerText.split("").map((char, index) => {
    if (char === " ") return `<br>`;
    return `<span class="letter">${char}</span>`;
  });
  element.value.innerHTML = newElement.join("");
};
const splittextWord = (element: Ref) => {
  let newElement = element.value.innerText.split(" ").map((word, index) => {
    return `<span class="word">${word + " "}</span>`;
  });
  element.value.innerHTML = newElement.join("");
};
onMounted(() => {
  //init state
  const initState = () => {
    splittextWord(text);
    splittextWord(text2);
    gsap.set(".text .word", { opacity: 0 });
    gsap.set(".text2 .word", { opacity: 0 });

    splittext(h3);

    gsap.set("h3 .letter", { x: -100, opacity: 0, rotate: -30 });

    gsap.set(".tag", { opacity: 0, translateX: -30 });
    gsap.set(".text", { opacity: 1 });
  };
  initState();

  //animate state

  const animateState = () => {
    gsap.to(".text .word", {
      opacity: 1,
      stagger: 0.04,
      duration: 0,
      delay: 1.5,
    });
    gsap.to(".text2 .word", {
      opacity: 1,
      stagger: 0.04,
      duration: 0,
      delay: 1.5,
    });

    gsap.to("h3 .letter", {
      x: 0,
      opacity: 1,
      rotate: 0,
      stagger: 0.03,
      duration: 0.75,
      ease: "elastic.out(1,0.5)",
      delay: 1.5,
    });

    gsap.to(".tag", {
      opacity: 1,
      translateX: 0,
      stagger: 0.1,
      duration: 0.5,
      delay: 2,
    });
  };
  animateState();
});
</script>

<template>
  <div class="text">
    <p ref="text">
      A city of contrasts where modernity meets tradition. From the bustling
      streets to the serene view of fuji-san, experience Japan's vibrant
      culture, iconic landmarks, and unforgettable adventures.
    </p>
    <div class="text2">
      <h3 ref="h3">Fuji San</h3>
      <p ref="text2">
        Tokyo thrills with city lights, rich culture, and Fuji-san views!
      </p>
    </div>
    <div class="flex">
      <div class="tag">
        <span>50°26'47.4"N</span>
        <span>1°18'37.6"W</span>
      </div>
      <div class="tag">
        <span>TP2024</span>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.text {
  margin-left: rem(24);
  font-size: rem(10);
  opacity: 0;
  position: relative;
  p {
    max-width: 230px;
  }
  .flex {
    display: flex;
    gap: rem(10);
    margin-top: rem(10);
  }

  .tag {
    display: flex;
    flex-direction: column;
    color: #d12f2d;
    border-radius: 50px;
    border: 1px solid #d12f2d;
    width: fit-content;
    padding-inline: rem(10);
    align-items: center;
    line-height: 1.2;
    &:nth-child(2) {
      color: #fff;
      background-color: #d12f2d;
      justify-content: center;
      font-weight: 900;
      padding-inline: rem(5);
      letter-spacing: 1px;
    }
  }
  .text2 {
    margin-top: rem(10);
    h3 {
      font-size: rem(16);
      font-weight: 700;
      text-transform: uppercase;
      .block {
        display: block;
      }
    }
    p {
      max-width: 100px;
    }

    @media screen and (min-width: 400px) {
      margin-top: unset;
      position: absolute;
      top: 0;
      translate: 0 -54px;
      left: 67%;
    }
  }
}
</style>
