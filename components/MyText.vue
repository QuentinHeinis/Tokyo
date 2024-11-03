<script lang="ts" setup>
import gsap from "gsap";
let text = ref();

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
    gsap.set(".text .word", { opacity: 0 });
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
  max-width: 230px;
  margin-left: rem(24);
  font-size: rem(10);
  opacity: 0;
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
}
</style>
