<template>
  <div class="flex flex-row items-center gap-7">
    <div
      class="h-6 w-6 transition-colors hover:cursor-pointer hover:fill-gray-800"
      @click="liked = !liked"
    >
      <LikedIcon v-if="liked" />
      <LikeIcon v-else />
    </div>

    <div class="w-4 transition-colors hover:cursor-pointer hover:fill-gray-800">
      <PreviousIcon @click="$emit('previous')" />
    </div>

    <div
      class="flex h-6 w-7 items-center transition-colors hover:cursor-pointer hover:fill-gray-800"
      @click="$emit('play')"
    >
      <PauseIcon v-if="playing" />
      <PlayIcon v-else />
    </div>

    <div class="w-4 transition-colors hover:cursor-pointer hover:fill-gray-800">
      <NextIcon @click="$emit('next')" />
    </div>
  </div>
</template>

<script setup lang="ts">
import LikeIcon from "./Icons/LikeIcon.vue";
import LikedIcon from "./Icons/LikedIcon.vue";
import NextIcon from "./Icons/NextIcon.vue";
import PreviousIcon from "./Icons/PreviousIcon.vue";
import PlayIcon from "./Icons/PlayIcon.vue";
import PauseIcon from "./Icons/PauseIcon.vue";
import { ref } from "vue";

defineProps({
  playing: {
    type: Boolean,
    required: true,
  },
});

const liked = ref(false);
defineEmits(["next", "previous", "play"]);
</script>
