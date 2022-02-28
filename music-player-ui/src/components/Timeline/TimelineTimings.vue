<template>
  <div class="flex flex-row justify-between font-light">
    <div>{{ currentTime }}</div>
    <div>{{ totalTime }}</div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  currentTime: {
    type: String,
    required: true,
  },
  totalTime: {
    type: String,
    required: true,
  },
});
</script>
