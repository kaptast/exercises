<template>
  <TimelineBar :progress="progress" />
  <TimelineTimings
    :current-time="currentTimeString"
    :total-time="totalTimeString"
  />
</template>

<script setup lang="ts">
import { computed } from "vue";
import TimelineBar from "./TimelineBar.vue";
import TimelineTimings from "./TimelineTimings.vue";

const props = defineProps({
  currentTime: {
    type: Number,
    required: true,
  },
  totalTime: {
    type: Number,
    required: true,
  },
});

const progress = computed(() => props.currentTime / props.totalTime);
const currentTimeString = computed(
  () =>
    `${Math.floor(props.currentTime / 60)}:${(props.currentTime % 60)
      .toString()
      .padStart(2, "0")}`
);
const totalTimeString = computed(
  () => `${Math.floor(props.totalTime / 60)}:${props.totalTime % 60}`
);
</script>
