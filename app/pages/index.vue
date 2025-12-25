<script setup lang="ts">
const posts = ref([
  {
    title: "Nuxt Icon v1",
    description: "Discover Nuxt Icon v1!",
    image: "https://nuxt.com/assets/blog/nuxt-icon/cover.png",
    date: "2024-11-25",
  },
  {
    title: "Nuxt 3.14",
    description: "Nuxt 3.14 is out!",
    image: "https://nuxt.com/assets/blog/v3.14.png",
    date: "2024-11-04",
  },
  {
    title: "Nuxt 3.13",
    description: "Nuxt 3.13 is out!",
    image: "https://nuxt.com/assets/blog/v3.13.png",
    date: "2024-08-22",
  },
  {
    title: "Nuxt 3.13",
    description: "Nuxt 3.13 is out!",
    image: "https://nuxt.com/assets/blog/v3.13.png",
    date: "2024-08-22",
  },
]);
</script>

<template>
  <!-- 使用 ClientOnly 确保在客户端 hydration 完成后再渲染，避免 SSR 时布局计算错误 -->
  <ClientOnly>
    <UBlogPosts :posts="posts" />
  </ClientOnly>
</template>
