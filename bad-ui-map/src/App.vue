<template>
  <div class="lg:relative flex flex-col h-screen w-screen">
    <Input @update-location="updateLocation()" class="order-1 md:order-2" />
    <Map v-bind="currentLocation" class="order-2 md:order-1" />
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
