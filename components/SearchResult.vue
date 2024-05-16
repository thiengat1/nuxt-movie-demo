<template>
  <div class="p-6">
    <div v-if="total" class="text-3xl">Search result for: {{ searchKey }}</div>
    <div v-if="total" class="text-gray-400">{{ total }} items</div>
    <div
      class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 mt-2 gap-2"
    >
      <div v-for="item in searchResult" :key="item.id">
        <firm-card :data="item" />
      </div>
    </div>
    <div v-if="allDataLoaded">All data loaded.</div>
  </div>
</template>

<script setup>
const props = defineProps({
  searchKey: {
    type: String,
    default: () => '',
  },
});
const searchResult = ref([]);
const allDataLoaded = ref(false);
const currentPage = ref(1);
const total = ref(0);

watch(
  () => props.searchKey,
  async (value) => {
    const res = await fetchData(1);
    if (res) {
      searchResult.value = res;
    }
  }
);
async function fetchData(page) {
  const res = await useFetch(
    `https://movies-proxy.vercel.app/tmdb/search/multi?query=${props.searchKey}&page=${page}&include_adult=false&language=en`
  );
  if (res.data) {
    total.value = res.data.value?.total_results;
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
    searchResult.value = [...searchResult.value, ...newData];
    currentPage.value++;
  } else {
    // If no more data is available, mark all data as loaded
    allDataLoaded.value = true;
  }
}
</script>

<style scoped></style>
