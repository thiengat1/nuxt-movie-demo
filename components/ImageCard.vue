<template>
  <div
    class="border-2 border-gray-500 border-solid hover:scale-105 transition-all duration-500 hover:cursor-pointer"
  >
    <img
      :src="`https://movies-proxy.vercel.app/ipx/f_webp&s_800x1200/tmdb/${imageSrc}`"
      class="object-contain"
    />
  </div>
</template>

<script setup>
const props = defineProps({
  imageSrc: {
    type: String,
    default: () => '',
  },
});
</script>

<style scoped></style>
