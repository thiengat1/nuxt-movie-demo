<template>
  <div class="relative bg-black aspect-[3/2] lg:aspect-[25/9]">
    <div class="z-0 absolute left-0 lg:left-1/3">
      <img
        :src="`https://movies-proxy.vercel.app/ipx/f_webp&s_2440x1318/tmdb/${data.backdrop_path}`"
        class="w-full h-full object-cover"
      />
    </div>
    <div
      class="flex absolute justify-center bottom-0 w-full lg:w-2/3 lg:h-full z-50 py-10 px-24 bg-gradient-to-t lg:bg-gradient-to-r from-50% from-black to-transparent"
    >
      <div
        class="flex flex-col gap-2 sm:gap-4 md:gap-6"
        v-motion="{
          initial: {
            y: 100,
            opacity: 0,
          },
          enter: {
            opacity: 1,
            y: 0,
            transition: {
              opacity: {
                duration: 1000,
              },
            },
          },
        }"
      >
        <div class="xs:text-xl md:text-3xl lg:text-5xl line-clamp-2">
          {{ data.title }}
        </div>
        <div class="text-[0.7rem] md:text-[1rem] flex items-center gap-2">
          <StarVote :data="data.vote_average" />
          <span class="text-gray-400">{{ data.vote_count }} reviews</span>
          <span class="text-gray-400">{{
            data.release_date?.substring(0, 4)
          }}</span>
          <span class="text-gray-400">{{
            `${convertToHours(data.runtime).hours}h ${
              convertToHours(data.runtime).minutes
            }min`
          }}</span>
        </div>
        <p class="text-[0.7rem] md:text-[1rem]">
          {{ data.overview }}
        </p>
        <button class="watchBtn">
          <Icon name="ph:play-light" size="22" />
          <span class="text-[0.7rem] md:text-[1rem]"> Watch Trailer</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { watch, ref } from 'vue';
const props = defineProps({
  movies: {
    type: Object,
    default: () => [],
  },
});

const { data } = useFetch(
  `https://movies-proxy.vercel.app/tmdb/movie/${props.movies[0].id}?append_to_response=videos,credits,images,external_ids,release_dates,combined_credits&include_image_language=en&language=en`,
  { cache: true }
);

function convertToHours(time) {
  var hours = Math.floor(time / 60);
  var minutes = time % 60;
  console.log('hours', hours);
  return { hours: hours, minutes: minutes };
}
</script>

<style scoped></style>
