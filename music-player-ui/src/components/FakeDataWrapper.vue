<template>
  <MusicPlayer
    v-bind="data"
    @next="next"
    @previous="previous"
    @play="data.playing = !data.playing"
  />
</template>

<script setup lang="ts">
import { reactive } from "vue";
import faker from "@faker-js/faker";
import MusicPlayer from "./MusicPlayer.vue";

const data = reactive({
  artist: "",
  songName: "",
  totalTime: 0,
  currentTime: 0,
  playing: true,
});

generateRandomSongData();

setInterval(playSong, 1000);

function next(): void {
  generateRandomSongData();
}

function previous(): void {
  generateRandomSongData();
}

function playSong(): void {
  if (!data.playing) {
    return;
  }

  if (data.currentTime >= data.totalTime) {
    return next();
  }

  data.currentTime += 1;
}

function generateRandomSongData(): void {
  data.artist = faker.random.words(getRandomInt(1, 5));
  data.songName = faker.random.words(getRandomInt(1, 7));
  data.totalTime = getRandomInt(60, 300);
  data.currentTime = 0;
}

function getRandomInt(min: number, max: number): number {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min) + min); //The maximum is exclusive and the minimum is inclusive
}
</script>
