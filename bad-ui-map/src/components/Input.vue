<template>
  <form
    @submit.prevent="tryToUpdateLocation()"
    class="md:absolute md:z-50 w-full md:w-[80%] lg:w-[40%] md:left-1/2 md:-translate-x-1/2 md:top-5 bg-slate-500/40 md:rounded-lg flex items-center space-y-1 md:space-y-3 flex-col p-2"
  >
    <h1 class="text-2xl">Driving</h1>
    <p class="text-center">
      Type "update" to update your current location on the map
    </p>
    <input type="text" class="rounded-md px-1 w-full" v-model="inputText" />
    <button type="submit" class="bg-slate-300 rounded-md py-2 px-6">
      Send
    </button>
  </form>
</template>

<script setup lang="ts">
  import { ref } from 'vue'

  const inputText = ref('')
  const emit = defineEmits(['updateLocation'])

  function tryToUpdateLocation(): void {
    if (inputText.value.trim().toLowerCase() === 'update') {
      inputText.value = ''
      emit('updateLocation')
    }
  }
</script>
