<template>
  <div class="p-2">
    <div class="ml-4 text-gray-400">{{ data.length }} videos</div>
    <div class="grid grid-cols-2 lg:grid-cols-3 xxl:grid-cols-4 gap-2">
      <div v-for="video in data" :key="video.id">
        <VideoCard :data="video" />
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
});
</script>

<style scoped></style>
