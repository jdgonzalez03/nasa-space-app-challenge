<template>
  <div class="map-container">
    <h1>Select a point on the map</h1>
    <small>Currently, this only works in Colombia</small>

    <div id="mapid" ref="mapContainer"></div>
    <Teleport to="body">
      <div id="imagen-api" v-if="isModalOpen" class="modal">
        <div class="modal-content">
          <img
            v-if="imageUrl"
            :src="imageUrl"
            alt="Imagen devuelta por el API"
            class="modal-image"
          />
          <p v-else>No image URL was received from the API.</p>
          <button @click="isModalOpen = false" class="close-button">Close</button>
        </div>
      </div>
    </Teleport>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import 'leaflet/dist/leaflet.css'
import L from 'leaflet'

const isModalOpen = ref(false)

const mapContainer = ref(null)
const imageUrl = ref(null)
let currentMarker = null

const BASE_URL = import.meta.env.VITE_API_URL

onMounted(() => {
  const mymap = L.map(mapContainer.value).setView([4.5709, -74.2973], 6)

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(mymap)

  function onMapClick(e) {
    const { lat, lng } = e.latlng
    isModalOpen.value = true // Cambié aquí para usar la referencia correctamente

    if (currentMarker) {
      mymap.removeLayer(currentMarker)
    }

    currentMarker = L.marker([lat, lng]).addTo(mymap)

    console.log('Latitud:', lat, 'Longitud:', lng)

    fetch(BASE_URL, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({ lat: lat, lon: lng })
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
  justify-content: flex-start;
  text-align: center;
  margin: 0 auto;
  max-width: 800px;
  padding: 20px;
}

h1 {
  font-size: 1.5rem;
  margin-bottom: 10px;
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

.modal {
  position: fixed;
  z-index: 9999;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.7); /* Fondo oscuro y semi-transparente */
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-content {
  position: relative;
  width: 1020px; /* Ancho fijo */
  background-color: white; /* Fondo blanco para el contenido */
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5); /* Sombra para el modal */
}

.modal-image {
  max-width: 100%;
  height: auto; /* Mantener la proporción */
}

.close-button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #007bff; /* Color azul para el botón */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.close-button:hover {
  background-color: #0056b3; /* Color más oscuro al pasar el ratón */
}
</style>
