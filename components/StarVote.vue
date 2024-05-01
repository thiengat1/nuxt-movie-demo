<template>
  <div class="flex items-center text-gray-400">
    <Icon
      v-for="item in vote"
      :key="`startVote${item}`"
      name="material-symbols-light:star"
      size="24"
      color="white"
    />

    <Icon
      v-for="item2 in voteEmpty"
      :key="`startEmpty${item2}`"
      name="material-symbols-light:star"
      size="24"
      color="grey"
    />

    <span class="ml-2">{{ data.toFixed(1) }}</span>
  </div>
</template>

<script setup>
import { computed } from 'vue';
const props = defineProps({
  data: {
    type: Object,
    default: () => 0,
  },
});

const vote = computed(() => {
  if (props.data) {
    return Math.round(props.data / 2);
  }
  return 0;
});
const voteEmpty = computed(() => {
  if (props.data) {
    return 5 - Math.round(props.data / 2);
  }
  return 0;
});
</script>

<style scoped></style>
