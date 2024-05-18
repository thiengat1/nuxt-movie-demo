<template>
  <div>
    <div
      class="videoCard flex gap-2 flex-col m-2 relative cursor-pointer"
      @click="handleOpenTrailer"
    >
      <div
        class="border-2 border-gray-500 border-solid hover:scale-105 transition-all duration-500 hover:cursor-pointer aspect-[16/9]"
      >
        <img
          :src="`https://movies-proxy.vercel.app/ipx/f_webp&s_800x1200/youtube/vi/${data.key}/maxresdefault.jpg`"
          class="object-cover h-full aspect-[16/9]"
        />
      </div>

      <div>{{ data?.character }}</div>
      <div class="text-gray-600">{{ data?.name }}</div>
      <Icon
        class="iconView absolute top-[50%] left-[50%] translate-x-[-100%] translate-y-[-100%] text-gray-400"
        size="40"
        name="ph:play-light"
      />
    </div>
    <TrailerWatch v-if="isOpen" @close="handleCloseTrailer" :videoInfo="data" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
const props = defineProps({
  data: {
    type: Object,
    default: () => {},
  },
});
const isOpen = ref(false);
function handleOpenTrailer() {
  isOpen.value = true;
}
function handleCloseTrailer() {
  console.log(3333);
  isOpen.value = false;
}
</script>

<style scoped>
.videoCard:hover .iconView {
  color: white;
}
</style>
