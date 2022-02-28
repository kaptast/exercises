<template>
  <MusicPlayer :current-time="currentTime" :total-time="totalTime" />
</template>

<script setup lang="ts">
import { ref } from "vue";
import MusicPlayer from "./MusicPlayer.vue";

const currentTime = ref(34);
const totalTime = ref(213);
</script>
