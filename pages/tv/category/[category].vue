<template>
  <div class="p-6">
    <div class="text-3xl">{{ title }}</div>
    <div
      class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 mt-2 gap-2"
    >
      <div v-for="item in dataResult" :key="item.id">
        <firm-card :data="item" />
      </div>
    </div>
    <div v-if="allDataLoaded">All data loaded.</div>
  </div>
</template>

<script setup>
import { ref, watch, onMounted, onUnmounted } from 'vue';
const dataResult = ref([]);
const allDataLoaded = ref(false);
const currentPage = ref(1);
const total = ref(0);
const { category } = useRoute().params;

const title = computed(() => {
  if (category === 'popular') {
    return 'Popular TV Shows';
  }
  if (category === 'top_rated') {
    return 'Top Rated TV Shows';
  }
  if (category === 'airing_today') {
    return 'TV Shows Airing Today';
  }
  return '';
});

onMounted(async () => {
  nextTick(async () => {
    const res = await fetchData(1);
    if (res) {
      dataResult.value = res;
    }
  });
});

async function fetchData(page) {
  const res = await useFetch(
    `https://movies-proxy.vercel.app/tmdb/tv/${category}?page=${page}&language=en`
  );
  if (res.data) {
    return res.data.value?.results;
  }
  return [];
}
onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});
onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});

async function handleScroll() {
  if (
    window.innerHeight + window.scrollY >= document.body.offsetHeight &&
    !allDataLoaded.value
  ) {
    await loadMore();
  }
}
async function loadMore() {
  const newData = await fetchData(currentPage.value + 1);
  if (newData.length > 0) {
    dataResult.value = [...dataResult.value, ...newData];
    currentPage.value++;
  } else {
    // If no more data is available, mark all data as loaded
    allDataLoaded = true;
  }
}
</script>

<style scoped></style>
