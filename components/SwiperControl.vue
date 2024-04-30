<template>
  <div class="flex justify-between">
    <button
      @click="swiper.slidePrev()"
      class="flex items-center justify-center top-0 z-50 left-0 w-20 bg-transparent hover:bg-[#00000080] opacity-0 hover:opacity-100 absolute h-[100%]"
    >
      <Icon name="bxs:left-arrow" size="32" />
    </button>
    <button
      @click="swiper.slideNext()"
      class="flex items-center justify-center top-0 z-50 right-0 w-20 bg-transparent hover:bg-[#00000080] opacity-0 hover:opacity-100 absolute h-[100%]"
    >
      <Icon name="bxs:right-arrow" size="32" />
    </button>
  </div>
</template>

<script setup lang="ts">
const swiper = useSwiper();
</script>

<style scoped></style>
