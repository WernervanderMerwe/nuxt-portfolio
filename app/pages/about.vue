<template>
  <article class="prose dark:prose-invert">
    <ContentRenderer v-if="post" :value="post" />
  </article>
</template>

<script setup lang="ts">
const { data: post } = await useAsyncData(
  `blog-${'about'}`,
  () => queryCollection('blog').path(`/blog/about`).first()
)
</script>