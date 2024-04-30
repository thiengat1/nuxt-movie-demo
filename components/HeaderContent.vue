<template>
  <div class="relative bg-black aspect-[3/2] lg:aspect-[25/9]">
    <div class="z-0 absolute left-0 lg:left-1/3">
      <img src="assets/images/app.webp" class="w-full h-full object-cover" />
    </div>
    <div
      class="flex absolute justify-center bottom-0 w-full lg:w-2/3 lg:h-full z-50 py-10 px-24 bg-gradient-to-t lg:bg-gradient-to-r from-50% from-black to-transparent"
    >
      <div
        class="flex flex-col gap-6"
        v-motion="{
          initial: {
            y: 100,
            opacity: 0,
          },
          enter: {
            y: 0,
            opacity: 1,
            transition: {
              opacity: {
                duration: 1000,
              },
            },
          },
        }"
      >
        <div class="xs:text-xl md:text-3xl lg:text-5xl line-clamp-2">
          Rebel Moon — Part Two: The Scargiver
        </div>
        <div class="text-[0.7rem] md:text-[1rem] flex items-center gap-2">
          <StarVote />
          <span class="text-gray-400">469 reviews</span>
          <span class="text-gray-400">2024</span>
          <span class="text-gray-400">3h 24min</span>
        </div>
        <p class="text-[0.7rem] md:text-[1rem]">
          The rebels gear up for battle against the ruthless forces of the
          Motherworld as unbreakable bonds are forged, heroes emerge — and
          legends are made.
        </p>
        <button class="watchBtn">
          <Icon name="ph:play-light" size="22" />
          <span class="text-[0.7rem] md:text-[1rem]"> Watch Trailer</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped></style>
