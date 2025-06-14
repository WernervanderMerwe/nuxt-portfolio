<template>
  <article class="prose dark:prose-invert">
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

useHead({
  title: slug?.toString().charAt(0)?.toUpperCase() + slug?.toString().slice(1) ?? 'Title'
})
</script>
