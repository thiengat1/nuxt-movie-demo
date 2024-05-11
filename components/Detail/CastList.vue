<template>
  <div class="p-4">
    <div class="text-2xl mb-4">Cast</div>
    <Swiper
      :modules="[SwiperAutoplay, SwiperEffectCreative]"
      :breakpoints="{
        200: { slidesPerView: 2 },
        400: { slidesPerView: 3 },
        640: { slidesPerView: 4 },
        768: { slidesPerView: 5 },
        1150: { slidesPerView: 6 },
        1280: { slidesPerView: 7 },
        1536: { slidesPerView: 8 },
      }"
      :loop="false"
      :effect="''"
      :autoplay="{
        delay: 8000,
        disableOnInteraction: true,
      }"
      :creative-effect="{
        prev: {
          shadow: false,
          translate: ['-20%', 0, -1],
        },
        next: {
          translate: ['100%', 0, 0],
        },
      }"
    >
      <SwiperSlide v-for="slide in data" :key="slide.id">
        <CastActor :data="slide" />
      </SwiperSlide>
      <swiper-control />
    </Swiper>
  </div>
</template>

<script setup>
import CastActor from './CastActor.vue';
const props = defineProps({
  data: {
    type: Object,
    default: () => [],
  },
});
</script>

<style scoped></style>
