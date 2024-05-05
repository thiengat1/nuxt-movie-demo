<template>
  <div>
    <MainPoster :data="movies?.results" type="movie" />
    <FirmCategories title="Popular Movies" :data="movies?.results" />
    <FirmCategories title="Top Rated Movies" :data="topRates?.results" />
    <FirmCategories title="Upcoming Movies" :data="upComings?.results" />
    <FirmCategories title="Now Playing Movies" :data="nowPlaying?.results" />
  </div>
</template>

<script setup lang="ts">
const { data: movies } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/movie/popular?page=1&language=en'
);
const { data: topRates } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/movie/top_rated?page=1&language=en'
);
const { data: upComings } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/movie/upcoming?page=1&language=en'
);
const { data: nowPlaying } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/movie/now_playing?page=1&language=en'
);
</script>

<style scoped></style>
