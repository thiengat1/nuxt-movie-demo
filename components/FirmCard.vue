<template>
  <div class="flex gap-2 flex-col m-2 cursor-pointer" @click="handleGoToDetail">
    <div
      class="w-40 md:w-60 border-2 border-gray-500 border-solid hover:scale-105 transition-all duration-500 hover:cursor-pointer"
    >
      <img
        :src="`https://movies-proxy.vercel.app/ipx/f_webp&s_800x1200/tmdb/${data.poster_path}`"
        class="object-contain"
      />
    </div>
    <div>{{ data.name || data.title }}</div>
    <star-vote class="ml-[-6px]" :data="data.vote_average" />
  </div>
</template>

<script setup>
const router = useRouter();
const props = defineProps({
  data: {
    type: Object,
    default: () => {},
  },
  type: {
    type: String,
    default: () => 'movie',
  },
});
const link =
  'https://movies-proxy.vercel.app/ipx/f_webp&s_800x1200/tmdb/cxevDYdeFkiixRShbObdwAHBZry.jpg';

function handleGoToDetail() {
  const { id } = useRoute().params;
  if (router.currentRoute.value?.path.includes(props.type) && id) {
    router.push({ path: `${props.data.id}` });
  } else {
    router.push({ path: `${props.type}/${props.data.id}` });
  }
}
</script>

<style scoped></style>
