<script lang="ts" setup>
import gsap from "gsap";
const line1 = ref();
const line2 = ref();
const splittext = (element: Ref) => {
  let newElement = element.value.innerText.split("").map((char, index) => {
    return `<span class="letter">${char}</span>`;
  });
  element.value.innerHTML = newElement.join("");
};
onMounted(() => {
  //init state
  const initState = () => {
    splittext(line1);
    splittext(line2);
    gsap.set("h2 .letter", { opacity: 0 });
    gsap.set("h2", { opacity: 1 });
  };
  initState();

  //animate state

  const animateState = () => {
    gsap.to("h2 .letter", {
      opacity: 1,
      stagger: 0.02,
      duration: 0,
      delay: 1.5,
    });
  };
  animateState();
});
</script>

<template>
  <h2>
    <span class="line" ref="line1">Journey to the heart </span>
    <span class="line" ref="line2">of fuji's beauty!</span>
  </h2>
</template>

<style lang="scss">
h2 {
  opacity: 0;
  padding-inline: rem(24);
  text-transform: uppercase;
  font-size: rem(18);
  margin-top: rem(10);
  display: flex;
  flex-direction: column;
}
</style>
