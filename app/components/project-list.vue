<template>
  <p class="mb-10">Take a Look at my GitHub projects!</p>
  <section v-if="pending">Loading...</section>
  <section v-else-if="error">Something Went Wrong... Try Again</section>
  <section v-else>
    <ul class="grid grid-cols-1 gap-4">
      <li
        v-for="repo in repos"
        :key="repo.id"
        class="border border-gray-200 rounded-sm p-4 hover:bg-gray-100 font-mono">
        <a
          :href="repo.html_url"
          target="_blank">
          <div class="flex items-center justify-between text-sm">
            <div class="font-semibold">{{ repo.name }}</div>
            <div class="">{{ repo.stargazers_count }}⭐</div>
          </div>
          <p class="text-sm">
            {{ repo.description }}
          </p>
        </a>
      </li>
    </ul>
  </section>
</template>

<script setup>
const { error, pending, data } = await useFetch(
  'https://api.github.com/users/WernervanderMerwe/repos'
);
const repos = computed(() =>
  data.value
    // .filter((r) => r.description)
    .sort((a, b) => {
      if (a.description && !b.description) return -1;
      if (!a.description && b.description) return 1;
      return 0;
    })
);
</script>
