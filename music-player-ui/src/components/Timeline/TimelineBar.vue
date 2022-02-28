<template>
  <div class="h-1 w-full rounded-full bg-black bg-opacity-50">
    <div class="relative h-full rounded-full bg-black" :style="width">
      <div
        class="absolute right-0 top-[-0.50rem] h-5 w-5 rounded-full bg-black"
      ></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from "vue";

const props = defineProps({
  progress: {
    type: Number,
    required: true,
  },
});

const width = computed(() => {
  return {
    width: `${props.progress * 100}%`,
  };
});
</script>
