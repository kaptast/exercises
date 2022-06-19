<template>
  <div class="relative">
    <Map v-bind="currentLocation" />
    <Input @update-location="updateLocation()" />
  </div>
</template>

<script setup lang="ts">
  import Map from './components/Map.vue'
  import Input from './components/Input.vue'
  import { onActivated, onMounted, reactive } from 'vue'

  const currentLocation = reactive({
    lat: 0,
    lon: 0,
  })

  function updateLocation(): void {
    navigator.geolocation.getCurrentPosition(
      (pos) => {
        currentLocation.lat = pos.coords.latitude
        currentLocation.lon = pos.coords.longitude
      },
      (err) => {
        console.error(err)
      }
    )
  }

  onMounted(() => setTimeout(() => updateLocation(), 500))
</script>
