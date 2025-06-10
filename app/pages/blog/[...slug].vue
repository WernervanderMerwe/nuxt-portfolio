<template>
  <article>
    <ContentRenderer v-if="post" :value="post" />
    <template v-else>
      <p>No content found.</p>
    </template>
  </article>
</template>

<script setup lang="ts">
const slug = useRoute().params.slug;
const { data: post } = await useAsyncData(
  `blog-${slug}`,
  () => queryCollection('blog').path(`/blog/${slug}`).first()
)
console.log(slug);
</script>
