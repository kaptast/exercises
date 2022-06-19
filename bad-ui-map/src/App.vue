<template>
  <div class="app lg:relative flex flex-col md:h-screen w-screen">
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

  onMounted(() => {
    setTimeout(() => updateLocation(), 500)

    const vh = window.innerHeight * 0.01
    document.documentElement.style.setProperty('--vh', `${vh}px`)
  })
</script>

<style scoped>
  @media screen and (max-width: 1023px) {
    .app {
      height: 100vh;
      height: calc(var(--vh, 1vh) * 100);
    }
  }
</style>
