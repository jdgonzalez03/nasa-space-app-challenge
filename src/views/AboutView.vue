<script setup>
import { ref } from 'vue'
import MemberTeam from '@/components/about/MemberTeam.vue'

const team = ref([
  {
    name: 'Lina Castañeda',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/lina-castañeda.jpeg',
    description:
      'Soy ingeniero Electrónico de Unillanos, con pasión por la innovación y los desafíos.'
  },
  {
    name: 'Hadid Villanueva',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/hadid-villanueva.jpeg',
    description:
      '¡Hola! Soy un ingeniero Electrónico de Unillanos, siempre preparado para enfrentar retos y desarrollar soluciones.'
  },
  {
    name: 'Juan Cruz',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/juan-cruz.jpg',
    description:
      'Hola, soy ingeniero Electrónico Unillanos, apasionado por innovar y resolver desafíos.'
  },
  {
    name: 'Jhonatan Sabogal',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/jhonatan-sabogal.jpg',
    description:
      'Soy un ingeniero Electrónico originario de Unillanos, listo para enfrentar desafíos y crear soluciones creativas.'
  },
  {
    name: 'Juan Gonzalez',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/juan-gonzalez.jpeg',
    description:
      '¡Hola! Soy un ingeniero Electrónico de Unillanos, entusiasta de los desafíos y la innovación'
  },
  {
    name: 'Jhoan Caicedo',
    ocuppation: 'Software Engineer',
    img: '/src/assets/team/jhoan-caicedo.jpeg',
    description:
      'Hola, soy ingeniero de software de Unillanos, siempre buscando nuevos desafíos y oportunidades de innovación'
  },
  {
    name: 'Daniel Martinez',
    ocuppation: 'Software Engineer',
    img: '/src/assets/team/daniel-martinez.jpeg',
    description:
      'Soy un ingeniero de software de Unillanos, apasionado por resolver problemas y crear soluciones innovadoras.'
  },
  {
    name: 'Yuberley Guerrero',
    ocuppation: 'Software Engineer',
    img: '/src/assets/team/yuberley.jpeg',
    description:
      '¡Hola! Soy ingeniero de software de Unillanos, siempre listo para innovar y enfrentar desafíos.'
  }
])
</script>

<template>
  <div class="about">
    <header>
      <h1>We are the people who make up CAPIPLANT UI</h1>
      <p>Our philosophy is simple: Keep working and enjoy!</p>
    </header>
    <main class="team">
      <MemberTeam
        v-for="(member, index) in team"
        :key="index"
        :name="member.name"
        :occupation="member.ocuppation"
        :img="member.img"
        :description="member.description"
      />
    </main>
  </div>
</template>

<style scoped>
.about {
  padding: 20px;
  font-family: Arial, sans-serif;
  text-align: center;
}

header {
  padding-top: 20px;
  margin-bottom: 20px;
}

header h1 {
  font-size: 2em;
  color: #333;
}

header p {
  font-size: 1.2em;
  color: #777;
  margin-top: 5px;
}

.team {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  justify-items: center;
  padding: 20px 0;
}
</style>
