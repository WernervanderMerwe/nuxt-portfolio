<template>
  <div class="container mx-auto 2xl">
    <header class="flex justify-between items-center mt-5">
      <div>
        <NuxtLink
          to="/"
          class="text-xl font-semibold p-2 hover:bg-gray-200">
          Werner van der Merwe
        </NuxtLink>
      </div>
      <Menu />
    </header>
    <main class="p-2">
      <slot />
    </main>
  </div>
</template>
