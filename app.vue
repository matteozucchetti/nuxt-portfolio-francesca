<template>
  <div>
    <div ref="loader" class="h-full w-full fixed bg-black z-20" />
    <NuxtPage class="h-dvh" />
  </div>
</template>

<script setup>
import gsap from "gsap";

const nuxtApp = useNuxtApp();
const loader = ref(null);
nuxtApp.hook("page:finish", () => {
  setTimeout(() => {
    gsap.to(loader.value, {
      duration: 1,
      opacity: 0,
      pointerEvents: "none",
    });
  }, 300);
});

useSeoMeta({
  title: "Francesca Da Forno | Portfolio",
  ogTitle: "Francesca Da Forno | Portfolio",
  description: "Senior Visual & UI Designer",
  ogDescription: "Senior Visual & UI Designer",
});

useHead({
  link: [
    {
      rel: "icon",
      type: "image/png",
      href: "/favicon.ico",
    },
  ],
});
</script>
