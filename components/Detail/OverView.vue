<template>
  <div class="flex gap-8 px-4">
    <div class="max-w-[300px] aspect-[10/16] hidden lg:block">
      <ImageCard :imageSrc="data?.poster_path" />
    </div>
    <div class="p-4">
      <div class="text-2xl mb-4">Storyline</div>
      <p class="text-gray-400">
        {{ data?.tagline }}
      </p>
      <ul class="grid grid-cols-[max-content_1fr] gap-4 mt-4 text-gray-400">
        <div>Genre</div>
        <div class="flex items-center gap-1">
          <div
            v-for="item in data?.genres"
            :key="item.id"
            class="bg-[#27282A] rounded-md py-1 px-2"
          >
            {{ item.name }}
          </div>
        </div>
        <div>Status</div>
        <div>{{ data?.status }}</div>
        <div>Language</div>
        <div>{{ data?.spoken_languages?.[0].name }}</div>
        <div>Production</div>
        <div>
          {{ data?.production_companies.map((item) => item.name).toString() }}
        </div>
      </ul>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: () => [],
  },
});
</script>

<style scoped></style>
