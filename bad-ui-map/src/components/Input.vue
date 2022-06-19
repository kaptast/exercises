<template>
  <div class="md:absolute o z-50 w-full lg:px-[40%] md:px-[20%] top-5">
    <div
      class="bg-slate-500/40 md:rounded-lg flex items-center space-y-1 md:space-y-3 flex-col p-2"
    >
      <h1 class="text-2xl">Driving</h1>
      <p class="text-center">
        Type "update" to update your current location on the map
      </p>
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
  import { ref } from 'vue'

  const inputText = ref('')
  const emit = defineEmits(['updateLocation'])

  function tryToUpdateLocation(): void {
    if (inputText.value.toLowerCase() === 'update') {
      inputText.value = ''
      emit('updateLocation')
    }
  }
</script>
