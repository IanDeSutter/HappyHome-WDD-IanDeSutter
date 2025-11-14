<template>
  <header class="card-header">
    <slot />
  </header>
</template>

<script setup>
</script>

<style scoped>
.card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.75rem;
}

.card-header h2 {
  font-size: 1.4rem;
  font-weight: 700;
}

.card-header a {
  border: none;
  background: transparent;
  cursor: pointer;
  font-size: 0.9rem;
  text-decoration: none;
  color: #000;
}
</style>
