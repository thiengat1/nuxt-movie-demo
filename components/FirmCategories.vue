<template>
  <div class="relative top-0 p-5">
    <div class="flex justify-between items-center">
      <div class="text-2xl">{{ title }}</div>
      <div class="text-gray-400 cursor-pointer hover:opacity-80">
        Explore more
      </div>
    </div>
    <categories-slider :data="data" :type="type" />
  </div>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: () => [],
  },
  title: {
    type: String,
    default: '',
  },
  type: {
    type: String,
    default: 'movie',
  },
});
</script>

<style scoped></style>
