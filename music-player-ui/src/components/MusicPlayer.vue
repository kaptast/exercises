<template>
  <div
    class="w-96 rounded-xl bg-[url(https://welovebudapest.com/i/aa/budapest-s-sites-on-the-unesco-world-heritage-list.inbox1600x528.jpg)] text-black shadow-lg"
  >
    <div
      class="rounded-l-xl bg-gradient-to-r from-teal-700 via-teal-700 to-transparent px-5 py-4"
    >
      <MusicPlayerBranding class="mb-2">
        <template #icon>
          <BrandIcon />
        </template>

        <template #default>
          <div>Music player</div>
          <template v-if="playlist">
            <div>|</div>
            <div>{{ playlist }}</div>
          </template>
        </template>
      </MusicPlayerBranding>

      <SongData class="mb-2" :artist="artist" :song-name="songName" />

      <MusicPlayerControls
        class="mb-10"
        @next="$emit('next')"
        @previous="$emit('previous')"
      />

      <SongTimeline :current-time="currentTime" :total-time="totalTime" />
    </div>
  </div>
</template>

<script setup lang="ts">
import MusicPlayerControls from "./MusicPlayerControls.vue";
import MusicPlayerBranding from "./MusicPlayerBranding.vue";
import BrandIcon from "./Icons/BrandIcon.vue";
import SongData from "./SongData.vue";
import SongTimeline from "./Timeline/SongTimeline.vue";

defineProps({
  currentTime: {
    type: Number,
    required: true,
  },
  totalTime: {
    type: Number,
    required: true,
  },
  artist: {
    type: String,
    required: true,
  },
  songName: {
    type: String,
    required: true,
  },
  playlist: {
    type: String,
    required: false,
    default: null,
  },
});

defineEmits(["next", "previous"]);
</script>
