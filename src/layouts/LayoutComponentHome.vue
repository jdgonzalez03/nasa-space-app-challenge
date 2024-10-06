<template>
  <div>
    <aside>
      <slot name="header"></slot>
    </aside>
    <section>
      <slot name="render"></slot>
    </section>
  </div>
</template>

<style scoped>
div {
  display: grid;
  grid-template-columns: 350px 1fr;
  min-height: 100vh;
}
section {
  background-color: var(--bg-color-render-page);
}
</style>
