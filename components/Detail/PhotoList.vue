<template>
  <div class="p-2 ml-4">
    <div class="flex gap-1 items-center mb-4">
      <div class="text-2xl">{{ title }}</div>
      <div class="ml-4 text-gray-400">{{ data.length }} images</div>
    </div>
    <div
      class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xxl:grid-cols-5 gap-4"
    >
      <div
        v-for="photo in data"
        :key="photo.id"
        class="border-2 border-gray-500 border-solid hover:scale-105 transition-all duration-500 hover:cursor-pointer"
      >
        <image-card :imageSrc="photo.file_path" />
      </div>
    </div>
  </div>
</template>

<script setup>
import VideoCard from './VideoCard';
const props = defineProps({
  data: {
    type: Object,
    default: () => [],
  },
  title: {
    type: String,
    default: () => '',
  },
});
</script>

<style scoped></style>
