<template>
  <div>
    <Detail type="tv" :data="detail" />
  </div>
</template>

<script setup>
import { watch, ref } from 'vue';
const { id } = useRoute().params;
console.log('id', id);
const props = defineProps({
  type: {
    type: String,
    default: 'movie',
  },
});

const link = `https://movies-proxy.vercel.app/tmdb/tv/${id}?append_to_response=videos,credits,images,external_ids,release_dates,combined_credits&include_image_language=en&language=en`;

const { data: detail } = useFetch(link, { cache: true });
</script>

<style scoped></style>
