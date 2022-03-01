<template>
  <MusicPlayer v-bind="data" />
</template>

<script setup lang="ts">
import { reactive } from "vue";
import MusicPlayer from "./MusicPlayer.vue";

const data = reactive({
  artist: "Sample artist",
  songName: "Sample song",
  totalTime: 213,
  currentTime: 134,
});
</script>
