<template>
  <div>
    <MainPoster :movies="movies.results" />
    <FirmCategories title="Popular Movies" :data="movies.results" />
    <FirmCategories title="Popular TV Shows" :data="tvShow.results" />
  </div>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue';
const detail = ref({});
const { data: movies, pending } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/movie/popular?page=1&language=en'
);
const { data: tvShow } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/tv/popular?page=1&language=en'
);
</script>

<style scoped></style>
