<template>
  <div class="flex gap-2 flex-col m-2">
    <image-card :imageSrc="data?.profile_path" />
    <div>{{ data?.character }}</div>
    <div class="text-gray-600">{{ data?.name }}</div>
  </div>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: () => {},
  },
});
</script>

<style scoped></style>
