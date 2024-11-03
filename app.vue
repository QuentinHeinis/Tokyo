<script setup lang="ts">
useHead({
  title: "Tokyo - Quentin Heinis",
  htmlAttrs: {
    lang: "en",
    translate: "no",
  },
  link: [
    {
      rel: "icon",
      type: "image/png",
      href: "/favicon.png",
    },
  ],
  meta: [
    { name: "google", content: "notranslate" },
    {
      name: "description",
      content:
        "Découvrez Tokyo et le Mont Fuji au travers de cette expérience visuel.",
    },
    { name: "author", content: "Quentin Heinis" },
    { name: "viewport", content: "width=device-width, initial-scale=1.0" },

    { property: "og:title", content: "Tokyo - Quentin Heinis" },
    { property: "og:type", content: "website" },
    { property: "og:url", content: "https://www.tokyo.heinis.dev" },

    { property: "og:image", content: "/TokyoFinal.png" },
    { property: "og:image:width", content: "1200" },
    { property: "og:image:height", content: "630" },
    { property: "og:image:alt", content: "Tokyo" },

    {
      property: "og:description",
      content:
        "Découvrez Tokyo et le Mont Fuji au travers de cette expérience visuel.",
    },
    { property: "og:site_name", content: "Tokyo - Quentin Heinis" },
    { property: "og:locale", content: "en_US" },

    { property: "twitter:card", content: "summary_large_image" },
    { property: "twitter:url", content: "https://www.tokyo.heinis.dev" },
    { property: "twitter:title", content: "Tokyo - Quentin Heinis" },
    {
      property: "twitter:description",
      content:
        "Découvrez Tokyo et le Mont Fuji au travers de cette expérience visuel.",
    },
    { property: "twitter:image", content: "/TokyoFinal.png" },
  ],
});
</script>

<template>
  <div class="wrapper">
    <Tokyo />
    <div class="myText">
      <MyTitle />
      <MySubTitle />
      <MyText />
    </div>
    <MyCity />
    <MyFooter />
    <MyBanner />
  </div>
</template>
<style lang="scss">
.wrapper {
  max-width: 800px;
  margin: 0 auto;
  overflow: hidden;
  position: relative;
  background: #fff;
  &::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: url("/grain.gif");
    mix-blend-mode: overlay;
    opacity: 0.3;
    background-size: cover;
    background-repeat: no-repeat;

    z-index: 50;
  }
  .myText {
    position: relative;
    width: 100%;
    @media screen and (min-width: 610px) {
      position: absolute;
    }
  }
}
</style>
