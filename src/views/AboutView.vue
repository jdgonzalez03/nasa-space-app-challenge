<script setup>
import { ref } from 'vue'
import MemberTeam from '@/components/about/MemberTeam.vue'

const team = ref([
  {
    name: 'Lina Castañeda',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/lina-castañeda.jpeg',
    description: 'Hola soy de unillanos y soy genial'
  },
  {
    name: 'Hadid Villanueva',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/hadid-villanueva.jpeg',
    description: 'Hola soy de unillanos y soy genial'
  },
  {
    name: 'Juan Cruz',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/juan-cruz.jpg',
    description: 'Hola soy de unillanos y soy genial'
  },
  {
    name: 'Jhonatan Sabogal',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/jhonatan-sabogal.jpg',
    description: 'Hola soy de unillanos y soy genial'
  },
  {
    name: 'Juan Gonzalez',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/juan-gonzalez.jpeg',
    description: 'Hola soy de unillanos y soy genial'
  },
  {
    name: 'Jhoan Caicedo',
    ocuppation: 'Software Engineer',
    img: '/src/assets/team/jhoan-caicedo.png',
    description: 'Hola soy de unillanos y soy genial'
  },
  {
    name: 'Daniel Martinez',
    ocuppation: 'Software Engineer',
    img: '/src/assets/team/daniel-martinez.png',
    description: 'Hola soy de unillanos y soy genial'
  },
  {
    name: 'Yuberley',
    ocuppation: 'Software Engineer',
    img: '/src/assets/team/yuberley.jpeg',
    description: 'Hola soy de unillanos y soy genial'
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
