<template>
  <div class="flex flex-row items-center gap-7">
    <div class="h-6 w-6">
      <LikeIcon />
    </div>

    <div class="w-4">
      <PreviousIcon @click="$emit('previous')" />
    </div>

    <div class="flex h-6 w-7 items-center" @click="$emit('play')">
      <PauseIcon v-if="playing" />
      <PlayIcon v-else />
    </div>

    <div class="w-4">
      <NextIcon @click="$emit('next')" />
    </div>
  </div>
</template>

<script setup lang="ts">
import LikeIcon from "./Icons/LikeIcon.vue";
import NextIcon from "./Icons/NextIcon.vue";
import PreviousIcon from "./Icons/PreviousIcon.vue";
import PlayIcon from "./Icons/PlayIcon.vue";
import PauseIcon from "./Icons/PauseIcon.vue";

defineProps({
  playing: {
    type: Boolean,
    required: true,
  },
});

defineEmits(["next", "previous", "play"]);
</script>
