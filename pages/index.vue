<template>
  <div>
    <MainPoster :data="movies?.results" type="movie" />
    <FirmCategories title="Popular Movies" :data="movies?.results" />
    <FirmCategories title="Popular TV Shows" :data="tvShow?.results" />
  </div>
</template>

<script setup>
const { data: movies } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/movie/popular?page=1&language=en'
);
const { data: tvShow } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/tv/popular?page=1&language=en'
);
</script>

<style scoped></style>
