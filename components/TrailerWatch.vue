<template>
  <div
    class="fixed w-full h-full top-0 left-0 bottom-0 right-0 z-[2000] bg-bgRgba flex justify-center"
  >
    <div
      class="w-[90%] lg:w-[70%] h-[30%] relative top-4 shadow-md bg-mainColor"
    >
      <div class="p-2 text-center text-xl">{{ videoInfo.name }}</div>
      <LiteYouTubeEmbed :id="videoInfo.key" title="123" />
      <Icon
        name="carbon:close-filled"
        size="28"
        color="white"
        class="absolute -right-4 -top-4 cursor-pointer hover:opacity-75"
        @click="handleClose"
      />
    </div>
  </div>
</template>

<script setup>
import LiteYouTubeEmbed from 'vue-lite-youtube-embed';
import 'vue-lite-youtube-embed/style.css';

const emits = defineEmits(['close']);
const props = defineProps({
  videoInfo: {
    type: Object,
    default: () => {},
  },
});

function handleClose() {
  emits('close');
}
</script>

<style scoped></style>
