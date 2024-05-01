<template>
  <div class="relative top-0 p-10">
    <div class="flex justify-between items-center">
      <div class="text-2xl">Popular TV Shows</div>
      <div class="text-gray-400 cursor-pointer hover:opacity-80">
        Explore more
      </div>
    </div>
    <categories-slider :data="data" />
  </div>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: () => [],
  },
});
</script>

<style scoped></style>
