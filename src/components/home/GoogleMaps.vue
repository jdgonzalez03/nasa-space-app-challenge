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
          <p v-else>Loading...</p>
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

const BASE_URL = import.meta.env.VITE_API_URL_PC

onMounted(() => {
  const mymap = L.map(mapContainer.value).setView([4.5709, -74.2973], 7)

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(mymap)

  function onMapClick(e) {
    const { lat, lng } = e.latlng
    isModalOpen.value = true // Cambié aquí para usar la referencia correctamente
    imageUrl.value = null

    if (currentMarker) {
      mymap.removeLayer(currentMarker)
    }

    currentMarker = L.marker([lat, lng]).addTo(mymap)

    console.log('Latitud:', lat, 'Longitud:', lng)
    fetch(`${BASE_URL}?lat=${lat}&lon=${lng}`, {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json'
      }
    })
      .then((data) => {
        console.log('Respuesta del servidor:', data)
        imageUrl.value = data.url || null
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
  max-width: 900px;
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
  height: 508px;
  width: 500px;
  margin-bottom: 20px;
  border: 4px solid #64e07b;
  border-radius: 20px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.modal {
  position: fixed;
  z-index: 9999;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.3); /* Fondo oscuro y semi-transparente */
  display: flex;
  align-items: center;
  padding-left: 300px;
  justify-content: flex-start;
}

.modal-content {
  position: relative;
  height: 490px;
  width: 600px; /* Ancho fijo */
  background-color: white; /* Fondo blanco para el contenido */
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5); /* Sombra para el modal */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.modal-image {
  max-width: 600px;
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
