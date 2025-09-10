<template>
    <div style="height:100vh; width:100vw">
        <lMap
            :zoom="11"
            :center="petropavl"
            :use-global-leaflet="false"
            style="height:100%; width:100%;"
        >
        <lTileLayer
            url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
            attribution="&copy; OpenStreetMap contributors"
        />

        <!-- City marker -->
        <lMarker :lat-lng="petropavl" :draggable="false">
        <lTooltip permanent direction="top">Petropavlovsk (NKR)</lTooltip>
        <lPopup>Petropavlovsk, North Kazakhstan Region</lPopup>
        </lMarker>

        <!-- Lakes marker-->
        <lMarker
            v-for="(lake, i) in lakes"
            :key="i"
            :lat-lng="[lake.lat, lake.lng]"
            :draggable="false"
        >
            <lTooltip permanent direction="top">{{ lake.name }}</lTooltip>
            <lPopup>
            <strong>{{ lake.name }}</strong><br />
            Transparency: {{ lake.level }}
            </lPopup>
        </lMarker>
        </lMap>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { LMap, LTileLayer, LMarker, LTooltip, LPopup } from '@vue-leaflet/vue-leaflet'
import 'leaflet/dist/leaflet.css'

type LatLngTuple = [number, number]

interface Lake {
  name: string
  lat: number
  lng: number
  level: number //transparency
}

// Map centre is Petropavlovsk
const petropavl = ref<LatLngTuple>([54.88, 69.16])

// List of lakes
const lakes = ref<Lake[]>([
  { name: 'Lake Pestroje', lat: 54.836699, lng: 69.111328, level: 1.4 },
  { name: 'Lake Beloje', lat: 54.927154, lng: 69.254322, level: 1.4 },
  { name: 'Lake Little Beloje', lat: 54.947154, lng: 69.328322, level: 1.2 },
  { name: 'Lake Cherepkovo', lat: 54.980154, lng: 69.358322, level: 1.3 },
  { name: 'Lake Penkovo', lat: 54.960154, lng: 69.258322, level: 1.4 },
  { name: 'Lake Gorkoje', lat: 54.947573, lng: 69.035463, level: 1.4 },
  { name: 'Lake Poganka', lat: 54.921025, lng: 69.035476, level: 1.5 },
  { name: 'Lake Dikoje', lat: 54.884106, lng: 69.113957, level: 1.75 },
])
</script>