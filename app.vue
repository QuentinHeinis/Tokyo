<script setup lang="ts">
useHead({
  title: "Tokyo - Quentin Heinis",
  htmlAttrs: {
    lang: "en",
  },
  link: [
    {
      rel: "icon",
      type: "image/png",
      href: "/favicon.png",
    },
  ],
  meta: [
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
  .myText {
    position: absolute;
    width: 100%;
  }
}
</style>
