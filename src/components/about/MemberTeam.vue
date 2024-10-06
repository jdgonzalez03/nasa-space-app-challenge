<script setup>
import { defineProps } from 'vue'

defineProps({
  name: String,
  occupation: String,
  img: String,
  description: String
})
</script>

<template>
  <article class="team-card">
    <figure class="team-card-image-wrapper">
      <img :src="img" :alt="`Imagen de ${name}`" class="team-card-image" />
    </figure>
    <h1 class="team-card-name">{{ name }}</h1>
    <h3 class="team-card-occupation">{{ occupation }}</h3>
    <p class="team-card-description">{{ description }}</p>
  </article>
</template>

<style scoped>
.team-card {
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
  max-width: 300px;
  text-align: center;
  font-family: Arial, sans-serif;
  transition: transform 0.3s;
}
.team-card:hover {
  transform: translateY(-5px);
  cursor: crosshair;
}
.team-card-image-wrapper {
  overflow: hidden;
  border-radius: 50%;
  width: 100px;
  height: 100px;
  margin: 0 auto 15px;
}
.team-card-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.team-card-name {
  font-size: 1.5em;
  color: #333;
  margin: 10px 0;
}
.team-card-occupation {
  font-size: 1.1em;
  color: #777;
  margin: 5px 0;
}
.team-card-description {
  font-size: 0.9em;
  color: #555;
}
</style>
