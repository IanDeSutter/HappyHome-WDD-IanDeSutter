<template>
  <div class="single-digit">
    <slot />
  </div>
</template>

<script setup>
</script>

<style scoped>
.single-digit {
  padding: 1rem 1.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 0.4rem;
  background-color: #f5f5f5;
  font-weight: 800;
  font-size: 4rem;
  color: #000;
}

@media (max-width: 600px) {
  .single-digit {
    padding: 0.6rem 1rem;
    font-size: 3rem;
  }
}

@media (max-width: 400px) {
  .single-digit {
    padding: 0.5rem 0.8rem;
    font-size: 2.4rem;
  }
}

.single-digit.is-loading {
  animation: blink 0.7s ease-in-out infinite alternate;
}

@keyframes blink {
  from {
    opacity: 1;
    transform: translateY(0px);
  }
  to {
    opacity: 0.3;
    transform: translateY(-2px);
  }
}
</style>
