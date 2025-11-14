<template>
  <section class="generic-card">
    <slot />
  </section>
</template>

<script setup>
</script>

<style scoped>
.generic-card {
  width: 100%;
  max-width: 520px;

  padding: 2rem 2.5rem;
  border-radius: 1.25rem;
  background-color: #ffffff;
  box-shadow: 0 18px 45px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  gap: 1.75rem;
  box-sizing: border-box;
}

@media (max-width: 480px) {
  .generic-card {

    padding: 1.5rem 1.25rem;
    gap: 1.25rem;
  }
}
</style>
