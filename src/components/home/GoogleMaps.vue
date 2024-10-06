<template>
  <div class="map-container">
    <h1>Seleccione un punto en el mapa</h1>
    <small>De momento esto solo funciona en Colombia</small>
    <div id="mapid" ref="mapContainer"></div>
    <div id="imagen-api">
      <img
        v-if="imageUrl"
        :src="imageUrl"
        alt="Imagen devuelta por el API"
        style="max-width: 100%"
      />
      <p v-else>No se recibió una URL de imagen del API.</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import 'leaflet/dist/leaflet.css'
import L from 'leaflet'

const mapContainer = ref(null)
const imageUrl = ref(null)
let currentMarker = null

onMounted(() => {
  const mymap = L.map(mapContainer.value).setView([4.5709, -74.2973], 6)

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(mymap)

  function onMapClick(e) {
    const { lat, lng } = e.latlng

    if (currentMarker) {
      mymap.removeLayer(currentMarker)
    }

    currentMarker = L.marker([lat, lng]).addTo(mymap)

    console.log('Latitud:', lat, 'Longitud:', lng)

    fetch('https://tu-endpoint.com/api', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({ latitud: lat, longitud: lng })
    })
      .then((response) => response.json())
      .then((data) => {
        console.log('Respuesta del servidor:', data)
        imageUrl.value = data.image_url || null
      })
      .catch((error) => {
        console.error('Error:', error)
        imageUrl.value = null
      })
  }

  mymap.on('click', onMapClick)
})
</script>

<style scoped>
.map-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  margin: 0 auto;
  max-width: 800px;
  padding: 20px;
}

h1 {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

small {
  font-size: 1rem;
  color: gray;
  margin-bottom: 20px;
}

#mapid {
  width: 100%;
  height: 500px;
  margin-bottom: 20px;
}

#imagen-api {
  width: 100%;
}
</style>
