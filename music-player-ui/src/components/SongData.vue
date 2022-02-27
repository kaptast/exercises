<template>
  <div>
    <div class="font-bold">{{ songName }}</div>
    <div class="font-light">{{ artist }}</div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  songName: {
    required: true,
    type: String,
  },
  artist: {
    required: true,
    type: String,
  },
});
</script>
