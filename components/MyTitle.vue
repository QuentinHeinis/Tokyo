<script lang="ts" setup>
import gsap from "gsap";
const first = ref();
const second = ref();
const third = ref();
const splittext = (element: Ref) => {
  let newElement = element.value.innerText.split("").map((char, index) => {
    if (char === " ") return `<span class="splitter"></span>`;
    return `<span class="letter">${char}</span>`;
  });
  element.value.innerHTML = newElement.join("");
};
onMounted(() => {
  //init state
  const initState = () => {
    splittext(first);
    splittext(second);
    splittext(third);
    gsap.set("h1 .letter", { x: -100, opacity: 0, rotate: -30 });
    gsap.set("h1", { opacity: 1 });
  };
  initState();
  //animate state
  const animateState = () => {
    gsap.to("h1 .letter", {
      x: 0,
      opacity: 1,
      rotate: 0,
      stagger: 0.03,
      duration: 0.75,
      ease: "elastic.out(1,0.5)",
      delay: 1.5,
    });
  };
  animateState();
});
</script>

<template>
  <h1>
    <span ref="first" class="first">Explore</span>
    <span ref="second" class="second">a vibrant</span>
    <span ref="third" class="third">culture</span>
  </h1>
</template>

<style lang="scss">
h1 {
  opacity: 0;
  font-weight: 700;
  font-style: normal;
  text-transform: uppercase;
  display: flex;
  width: 100%;
  flex-direction: column;
  padding-inline: rem(24);
  position: relative;
  font-size: rem(24);

  .splitter {
    display: block;
    width: 25px;
  }
  .first {
    display: flex;
  }
  .second {
    color: #d12f2d;
    display: flex;
    width: 100%;
    max-width: 350px;
    justify-content: flex-end;
  }
  .third {
    display: flex;
  }
  @media screen and (min-width: 610px) {
    flex-direction: row;
    font-size: rem(32);
    .first {
      margin-right: 100px;
    }
    .second {
      max-width: unset;
      justify-content: unset;
    }
  }
}
</style>
