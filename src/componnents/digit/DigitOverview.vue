<template>
  <div class="digit-overview">
    <slot />
  </div>
</template>

<script setup>
</script>

<style scoped>
.digit-overview {
  display: flex;
  gap: 0.75rem;
  justify-content: center;
  margin: 0.75rem 0 1rem;
  flex-wrap: nowrap;
}

@media (max-width: 600px) {
  .digit-overview {
    gap: 0.5rem;
    flex-wrap: wrap;
  }
}
</style>
