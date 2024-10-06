<script setup>
import { ref } from 'vue'
import MemberTeam from '@/components/about/MemberTeam.vue'

const team = ref([
  {
    name: 'Lina Castañeda',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/lina-castañeda.jpeg',
    description:
      'I am an Electronic Engineer from Unillanos, passionate about innovation and challenges.'
  },
  {
    name: 'Juan Cruz',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/juan-cruz.jpg',
    description:
      'Hello, I am an Electronic Engineer from Unillanos, passionate about innovating and solving challenges.'
  },
  {
    name: 'Jhonatan Sabogal',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/jhonatan-sabogal.jpg',
    description:
      'I am an Electronic Engineer from Unillanos, ready to tackle challenges and create creative solutions.'
  },
  {
    name: 'Juan Gonzalez',
    ocuppation: 'Electronic Engineer',
    img: '/src/assets/team/juan-gonzalez.jpeg',
    description:
      'Hi! I am an Electronic Engineer from Unillanos, enthusiastic about challenges and innovation.'
  },
  {
    name: 'Jhoan Caicedo',
    ocuppation: 'Software Engineer',
    img: '/src/assets/team/jhoan-caicedo.jpeg',
    description:
      'Hello, I am a Software Engineer from Unillanos, always looking for new challenges and opportunities for innovation.'
  },
  {
    name: 'Daniel Martinez',
    ocuppation: 'Software Engineer',
    img: '/src/assets/team/daniel-martinez.jpeg',
    description:
      'I am a Software Engineer from Unillanos, passionate about solving problems and creating innovative solutions.'
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
  max-width: 1024px;
  grid-template-columns: repeat(3, minmax(250px, 1fr));
  gap: 20px;
  justify-items: center;
  padding: 20px 0;
}
</style>
