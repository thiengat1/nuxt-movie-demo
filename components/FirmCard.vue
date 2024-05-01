<template>
  <div class="flex gap-2 flex-col m-2">
    <div
      class="w-40 md:w-60 border-2 border-gray-500 border-solid hover:scale-105 transition-all duration-500 hover:cursor-pointer"
    >
      <img
        :src="`https://movies-proxy.vercel.app/ipx/f_webp&s_800x1200/tmdb/${data.poster_path}`"
        class="object-contain"
      />
    </div>
    <div>{{ data.name || data.title }}</div>
    <star-vote class="ml-[-6px]" :data="data.vote_average" />
  </div>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: () => [],
  },
});
const link =
  'https://movies-proxy.vercel.app/ipx/f_webp&s_800x1200/tmdb/cxevDYdeFkiixRShbObdwAHBZry.jpg';
</script>

<style scoped></style>
