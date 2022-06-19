<template>
  <div class="absolute z-50 w-full px-96 top-5">
    <div
      class="bg-slate-500/40 rounded-lg flex items-center space-y-3 flex-col p-2"
    >
      <h1 class="text-2xl">Driving</h1>
      <p>Type "update" to update your current location on the map</p>
      <input type="text" class="rounded-md px-1 w-full" v-model="inputText" />
      <button
        type="button"
        class="bg-slate-300 rounded-md py-2 px-6"
        @click="tryToUpdateLocation()"
      >
        Send
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
  import { ref, defineEmits } from 'vue'

  const inputText = ref('')
  const emit = defineEmits(['updateLocation'])

  function tryToUpdateLocation(): void {
    if (inputText.value.toLowerCase() === 'update') {
      inputText.value = ''
      emit('updateLocation')
    }
  }
</script>
