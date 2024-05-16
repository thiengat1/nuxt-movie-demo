<template>
  <div
    class="z-[1000] lg:w-[80px] bg-black fixed bottom-0 lg:left-0 w-full lg:h-[100vh] border border-solid border-[#9ca3af33] rounded-l-md"
  >
    <div
      class="h-full flex py-2 lg:py-0 lg:flex-col justify-evenly items-center gap-12"
    >
      <NuxtLink
        v-for="menu in menus"
        :key="menu.name"
        :to="menu.link"
        @click="() => handleMenuClick(menu.id)"
      >
        <Icon class="menuIcon" :name="menu.icon" size="32" />
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const selected = ref(1);
const menus = [
  { id: 1, name: 'home', icon: 'ic:round-home', link: '/' },
  { id: 2, name: 'movie', icon: 'pixelarticons:movie', link: '/movie' },
  { id: 3, name: 'tv', icon: 'pepicons-pencil:television', link: '/tv' },
  { id: 4, name: 'search', icon: 'ic:outline-search', link: '/search' },
];
function handleMenuClick(id) {
  selected.value = id;
}
</script>

<style scoped>
.router-link-exact-active {
  color: #12b488;
}
</style>
