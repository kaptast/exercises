<template>
  <div class="md:h-screen h-full w-screen relative inset-0 z-0">
    <l-map ref="map" v-model:zoom="zoom" :center="[lat, lon]">
      <l-tile-layer
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
        layer-type="base"
        name="OpenStreetMap"
        attribution="&copy; <a href='https://www.openstreetmap.org/copyright'>OpenStreetMap</a> contributors"
      ></l-tile-layer>
      <l-marker :lat-lng="[lat, lon]"></l-marker>
    </l-map>
  </div>
</template>

<script setup lang="ts">
  import 'leaflet/dist/leaflet.css'
  import { LMap, LTileLayer, LMarker } from '@vue-leaflet/vue-leaflet'
  import { ref } from 'vue'

  const zoom = ref(17)

  defineProps<{
    lat: number
    lon: number
  }>()
</script>
