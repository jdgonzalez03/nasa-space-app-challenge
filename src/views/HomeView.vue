<script setup>
import GoogleMaps from '@/components/home/GoogleMaps.vue'
import TableItems from '@/components/home/TableItems.vue'
</script>

<template>
  <main>
    <GoogleMaps />
    <TableItems />
  </main>
</template>

<style scoped>
main {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
