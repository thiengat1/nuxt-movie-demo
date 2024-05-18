<template>
  <div class="py-4">
    <Swiper
      :modules="[SwiperAutoplay, SwiperEffectCreative]"
      :breakpoints="{
        150: { slidesPerView: 1 },
        250: { slidesPerView: 2 },
        640: { slidesPerView: 3 },
        768: { slidesPerView: 3 },
        1150: { slidesPerView: 4 },
        1280: { slidesPerView: 5 },
        1536: { slidesPerView: 6 },
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
        <FirmCard :data="slide" :type="type" />
      </SwiperSlide>
      <swiper-control />
    </Swiper>
  </div>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: () => [],
  },
  type: {
    type: String,
    default: 'movie',
  },
});
</script>

<style scoped></style>
