<template>
  <div class="data-table">
    <h1>Meteorological Data</h1>
    <small>To take in mind</small>
    <table>
      <thead>
        <tr>
          <th>Precipitation Range (mm)</th>
          <th>Cloud Fraction Range (%)</th>
          <th>Pressure Range (hPa)</th>
          <th>Interpretation</th>
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

const weatherData = ref([
  {
    precipitation: '0-2',
    cloudFraction: '0-20',
    pressure: '1000-1015',
    description: 'Mostly dry weather; little to no rain. Low chance of clouds.'
  },
  {
    precipitation: '2 - 10',
    cloudFraction: '20 - 40',
    pressure: '1015 - 1025',
    description: 'Slightly humid weather; possibility of drizzle. Scattered clouds.'
  },
  {
    precipitation: '10 - 25',
    cloudFraction: '40 - 60',
    pressure: '1025 - 1035',
    description: 'Moderately humid weather; light rain is likely. Denser clouds.'
  },
  {
    precipitation: '25 - 50',
    cloudFraction: '60 - 80',
    pressure: '1035 - 1045',
    description: 'Humid weather; frequent and abundant rains. Layered or cumulus clouds.'
  },
  {
    precipitation: '50 - 100',
    cloudFraction: '80 - 100',
    pressure: '1045 - 1055',
    description: 'Very humid weather; intense rains and potential for storms. High cloud coverage.'
  },
  {
    precipitation: '> 100',
    cloudFraction: 100,
    pressure: '< 1045',
    description: 'Extremely humid weather; risk of flooding. Very dense and stormy clouds.'
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
}

th,
td {
  border: 1px solid #ccc;
  padding: 5px; /* Reducido */
  text-align: center;
  font-size: 0.75rem; /* Reducido */
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
