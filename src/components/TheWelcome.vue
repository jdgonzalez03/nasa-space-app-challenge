<script setup></script>

<template>
  <div class="container">
    <figure class="colombia-gradient">
      <img src="@/assets/logo-chigui.png" alt="Logo" />
    </figure>
    <h1>Capi<span>Plant</span></h1>
  </div>
</template>

<style scoped>
.container {
  min-height: 100vh;
  background-color: var(--bg-color-bar-side);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

h1 {
  font-size: 2rem;
  font-weight: bold;
  color: #fff;
  text-transform: uppercase;
  letter-spacing: 1px;
  text-align: center;
  margin-top: 10px;
}

span {
  font-weight: bold;
}

figure img {
  width: 200px;
  rotate: -80deg;
  animation: pulse 3s ease-in-out;
}

@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
  100% {
    transform: scale(1);
  }
}
</style>
