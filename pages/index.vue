<template>
  <div>
    <MainPoster :data="detail" />
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
onMounted(() => {
  let delayGet = setInterval(async () => {
    if (movies.value.results) {
      clearInterval(delayGet);
      const res = await useFetch(
        `https://movies-proxy.vercel.app/tmdb/movie/${movies.value?.results[0].id}?append_to_response=videos,credits,images,external_ids,release_dates,combined_credits&include_image_language=en&language=en`,
        { cache: true }
      );
      detail.value = res.data.value;
    }
  });
});
</script>

<style scoped></style>
