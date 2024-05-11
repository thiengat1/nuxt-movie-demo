<template>
  <div>
    <MainPoster :data="popularShow?.results" type="tv" :isLoadData="true" />
    <FirmCategories
      title="Popular TV Shows"
      :data="popularShow?.results"
      type="tv"
    />
    <FirmCategories
      title="Top Rated TV Shows"
      :data="topRates?.results"
      type="tv"
    />
    <FirmCategories
      title="TV Shows Airing Today"
      :data="airingToday?.results"
      type="tv"
    />
  </div>
</template>

<script setup lang="ts">
const { data: popularShow } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/tv/popular?page=1&language=en'
);
const { data: topRates } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/tv/top_rated?page=1&language=en'
);
const { data: airingToday } = useFetch(
  'https://movies-proxy.vercel.app/tmdb/tv/airing_today?page=1&language=en'
);
</script>

<style scoped></style>
