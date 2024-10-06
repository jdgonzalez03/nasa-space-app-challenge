<template>
  <div class="data-table">
    <h1>Datos Meteorológicos</h1>
    <small>A tener en cuenta</small>
    <table>
      <thead>
        <tr>
          <th>Precipitación Promedio (mm)</th>
          <th>Fracción de Nubes Promedio (%)</th>
          <th>Presión en la Parte Superior de las Nubes (hPa)</th>
          <th>Descripción</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(data, index) in weatherData" :key="index">
          <td>{{ data.precipitation }}</td>
          <td>{{ data.cloudFraction }}</td>
          <td>{{ data.pressure }}</td>
          <td>{{ data.description }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Datos de ejemplo
const weatherData = ref([
  {
    precipitation: 12,
    cloudFraction: 75,
    pressure: 1015,
    description: 'Lluvia leve en promedio.'
  },
  {
    precipitation: 5,
    cloudFraction: 50,
    pressure: 1020,
    description: 'Pocas nubes, condiciones mayormente despejadas.'
  },
  {
    precipitation: 0,
    cloudFraction: 10,
    pressure: 1010,
    description: 'Sin precipitación, cielo despejado.'
  },
  {
    precipitation: 25,
    cloudFraction: 90,
    pressure: 1005,
    description: 'Lluvia moderada a fuerte.'
  },
  {
    precipitation: 15,
    cloudFraction: 60,
    pressure: 1018,
    description: 'Condiciones nubladas con lluvia ocasional.'
  }
])
</script>

<style scoped>
.data-table {
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
  text-align: center;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
}

th,
td {
  border: 1px solid #ccc;
  padding: 5px; /* Reducido */
  text-align: center;
  font-size: 0.875rem; /* Reducido */
}

th {
  background-color: #f2f2f2;
}

small {
  font-size: 1rem;
  color: gray;
  margin-bottom: 20px;
}
</style>
