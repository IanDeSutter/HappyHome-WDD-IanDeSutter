<template>
  <footer class="card-footer">
    <a
      href="#"
      class="get-new-code"
      :class="{ 'is-loading': loading }"
      :aria-disabled="loading"
      :tabindex="loading ? -1 : 0"
      @click.prevent="emit('get-new-code')"
    >
      <span v-if="loading" class="loader-icon"></span>
      <span v-else>Get new Code</span>
    </a>
    <p>
      Your access code is unique for your apartment. If you generate a new code,
      the old code can not be used anymore.
    </p>
  </footer>
</template>

<script setup>
const props = defineProps({
  loading: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(["get-new-code"]);
</script>

<style scoped>
.card-footer {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  font-size: 0.9rem;
  color: #4b5563;
}

.get-new-code {
  padding: 0.7rem 0;
  border-radius: 0;
  border: none;
  background: #3014ff;
  color: #ffffff;
  cursor: pointer;
  font-weight: 500;
  font-size: 0.85rem;
  text-align: center;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.card-footer a + p {
  margin-top: 0.4rem;
  font-size: 0.7rem;
  color: #9ca3af;
  line-height: 1.4;
}

.card-footer::after {
  content: "";
  display: block;
  height: 0.4rem;
  margin-top: -0.35rem;
}

.get-new-code.is-loading {
  opacity: 0.7;
  cursor: default;
  pointer-events: none;
}

.loader-icon {
  width: 20px;
  height: 20px;
  border-radius: 999px;
  border: 3px solid #fff;
  border-top-color: transparent;
  box-sizing: border-box;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
