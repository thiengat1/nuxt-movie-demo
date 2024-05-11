<template>
  <div class="relative top-0">
    <main-poster :currentData="data" />
    <div class="flex justify-center gap-8 mt-8 text-2xl mb-12">
      <div
        v-for="tab in tabs"
        :key="tab.id"
        :class="` ${
          tabActive === tab.id ? 'tab' : ' text-gray-500 cursor-pointer'
        }`"
        @click="() => handleTabClick(tab.id)"
      >
        {{ tab.name }}
      </div>
    </div>
    <OverView :data="data" />
    <VideoList v-if="tabActive === 2" :data="data?.videos?.results" />
    <PhotosMain v-if="tabActive === 3" :data="data" />
    <CastList :data="data?.credits?.cast" />
    <firm-categories
      title="More like this"
      :data="recommendation"
      :type="type"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import CastList from './CastList.vue';
import OverView from './OverView.vue';
import VideoList from './VideoList.vue';
import PhotosMain from './PhotosMain.vue';

const tabs = [
  { id: 1, name: 'OVERVIEW' },
  { id: 2, name: 'VIDEOS' },
  { id: 3, name: 'PHOTOS' },
];

const tabActive = ref(1);

const props = defineProps({
  type: {
    type: String,
    default: 'movie',
  },
  data: {
    type: Object,
    default: () => {},
  },
  recommendation: {
    type: Object,
    default: () => [],
  },
});

function handleTabClick(id) {
  tabActive.value = id;
}
</script>

<style scoped></style>
