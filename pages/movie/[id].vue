<template>
  <div>
    <Detail
      type="movie"
      :data="detail"
      :recommendation="recommendation?.results"
    />
  </div>
</template>

<script setup>
const { id } = useRoute().params;

const props = defineProps({
  type: {
    type: String,
    default: 'movie',
  },
});

const link = `https://movies-proxy.vercel.app/tmdb/movie/${id}?append_to_response=videos,credits,images,external_ids,release_dates,combined_credits&include_image_language=en&language=en`;

const { data: detail } = useFetch(link, { cache: true });

const { data: recommendation } = useFetch(
  `https://movies-proxy.vercel.app/tmdb/movie/${id}/recommendations?page=1&language=en`
);
</script>

<style scoped></style>
