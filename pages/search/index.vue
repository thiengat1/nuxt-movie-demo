<template>
  <div>
    <div class="relative w-ful flex items-center justify-center">
      <Icon
        name="ic:outline-search"
        size="40"
        class="absolute left-4"
        color="grey"
      />
      <input
        @input="handleInput"
        autofocus
        placeholder="Type to search"
        class="w-full bg-[#1F2021] border-none outline-none py-5 px-[60px] text-2xl"
      />
    </div>
    <div>
      <search-result :searchKey="searchKey" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import _ from 'lodash';
const searchKey = ref();

function handleInput(e) {
  debouncedSearch(e.target.value);
}
const debouncedSearch = _.debounce(async (value) => {
  searchKey.value = value;
}, 500);
</script>

<style scoped></style>
