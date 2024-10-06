<script setup>
import { RouterLink, RouterView } from 'vue-router'
import LayoutComponentHome from '@/layouts/LayoutComponentHome.vue'
</script>

<template>
  <LayoutComponentHome>
    <template #header>
      <header>
        <figure class="colombia-gradient">
          <img class="logo-gradient" src="@/assets/logo-chigui.png" alt="Logo" />
        </figure>
        <h1>CapiPlant</h1>
        <small>Made by Colombian Engineers</small>

        <ul class="logos">
          <li>
            <img class="logo" src="@/assets/logo-nasa-2.png" alt="Logo IEEE" />
          </li>
          <li>
            <img class="logo" src="@/assets/logo-nasa.png" alt="Logo NASA" />
          </li>
          <li>
            <img class="logo" src="@/assets/logo-unillanos.png" alt="Logo Unillanos" />
          </li>
        </ul>

        <nav>
          <RouterLink to="/">
            <i class="bi bi-info-circle"></i>
            Home
          </RouterLink>
          <RouterLink to="/about">
            <i class="bi bi-paperclip"></i>
            About Us
          </RouterLink>
          <RouterLink to="/what-is">
            <i class="bi bi-archive"></i>
            What is this project?
          </RouterLink>
        </nav>

        <figure>
          <img class="logo-ieee" src="@/assets/logo-ieee.png" alt="Logo IEEE" />
        </figure>
      </header>
    </template>

    <template #render>
      <main>
        <RouterView />
        <img class="cafe" src="@/assets/cafecito.png" alt="Cafe" />
      </main>
    </template>
  </LayoutComponentHome>
</template>

<style scoped>
/*Header*/
header {
  padding: 24px;
  background: linear-gradient(to bottom, var(--bg-color-bar-side) 75%, #fff);
  color: #fff;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  gap: 18px;
}

h1 {
  font-size: 1.8rem;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 1px;
  text-align: center;
}

small {
  color: #c8c8c8;
}

/*Logos*/
ul,
li {
  text-decoration: none;
  list-style: none;
}

ul {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 32px;
}

.logo {
  height: 60px;
  width: 60px;
  object-fit: cover;
}

/*Nav*/

nav {
  margin-top: 8px;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: left;
}

a {
  color: #fff;
  text-decoration: none;
  padding-bottom: 8px;
  padding-top: 8px;
  border-top: 1px solid #fff;
}

a:last-child {
  border-bottom: 1px solid #fff;
}

i {
  width: 16px;
  height: 16px;
  padding: 1px 3px;
  margin-right: 12px;
  border-radius: 50%;
}

.bi-info-circle {
  background-color: #00ee5f;
}

.bi-paperclip {
  background-color: #ff4b4b;
}

.bi-archive {
  background-color: #ad5bff;
}

/*logo*/
.logo-ieee {
  position: absolute;
  bottom: 0;
  left: 55px;
  width: 220px;
}

/*Main*/
main {
  background-color: var(--bg-color-render-page);
  min-height: 100vh;
}

.cafe {
  position: absolute;
  width: 120px;
  bottom: 0;
  right: 0;
}
</style>
