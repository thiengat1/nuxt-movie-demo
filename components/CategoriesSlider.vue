<template>
  <div class="py-4">
    <Swiper
      :modules="[SwiperAutoplay, SwiperEffectCreative]"
      :breakpoints="{
        200: { slidesPerView: 1 },
        400: { slidesPerView: 2 },
        700: { slidesPerView: 3 },
        1000: { slidesPerView: 4 },
        1300: { slidesPerView: 5 },
        1600: { slidesPerView: 6 },
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
      <SwiperSlide v-for="slide in 10" :key="slide">
        <FirmCard />
      </SwiperSlide>
      <swiper-control />
    </Swiper>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped></style>
