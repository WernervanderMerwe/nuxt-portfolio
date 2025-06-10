<template>
    <div class="flex space-x-2 items-center">
        <div class="text-gray-500 text-xs" v-if="showNextModeLabel">Change to {{ nextMode }}</div>
        <button
          @click="toggleMode"
          @mouseenter="showNextModeLabel = true"
          @mouseleave="showNextModeLabel = false"
          class="hover:bg-gray-200 dark:hover:bg-gray-600 px-2 py-1 text-gray-500 rounded-lg">
          {{ nextModeIcon }}
        </button>
    </div>
</template>

<script setup>
const colorMode = useColorMode();

const modes = ['system', 'light', 'dark'];
const nextModeIcons = {
  system: '🌓',
  light: '🌕',
  dark: '🌑',
};
const showNextModeLabel = ref(false);
const nextMode = computed(() => {
  const currentModeIndex = modes.indexOf(colorMode.preference);
  const nextIndex =
    currentModeIndex + 1 === modes.length ? 0 : currentModeIndex + 1;
  return modes[nextIndex];
});
const nextModeIcon = computed(() => nextModeIcons[nextMode.value]);
const toggleMode = () => (colorMode.preference = nextMode.value);
</script>
