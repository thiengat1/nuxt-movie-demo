<template>
  <div>
    <PhotoList title="Backdrops" :data="data?.images?.backdrops" />
    <PhotoList title="Posters" :data="data?.images?.posters" />
  </div>
</template>

<script setup>
import PhotoList from './PhotoList';

const props = defineProps({
  data: {
    type: Object,
    default: () => {},
  },
});
</script>

<style scoped></style>
