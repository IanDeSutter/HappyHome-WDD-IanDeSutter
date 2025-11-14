<template>
  <main>
    <header class="app-header">
      <div class="app-header__home">
        <Home class="app-header__icon" />
        <span class="app-header__title">Happy home</span>
      </div>
    </header>

    <GenericCard>
      <GenericCardHeader>
        <h2>Your access code:</h2>
        <a href="#" aria-label="Close">
          <X class="close-icon" />
        </a>
      </GenericCardHeader>

      <DigitOverview>
        <SingleDigit
          v-for="(digit, index) in code"
          :key="index"
          :class="{ 'is-loading': isLoading }"
        >
          {{ isLoading ? "*" : digit }}
        </SingleDigit>
      </DigitOverview>

      <GenericCardFooter
        :loading="isLoading"
        @get-new-code="handleGetNewCode"
      />
    </GenericCard>
  </main>
</template>

<script setup>
import { ref } from "vue";
import { Home, X } from "lucide-vue-next";
import GenericCard from "./componnents/generic/GenericCard.vue";
import GenericCardHeader from "./componnents/generic/GenericCardHeader.vue";
import DigitOverview from "./componnents/digit/DigitOverview.vue";
import SingleDigit from "./componnents/digit/SingleDigit.vue";
import GenericCardFooter from "./componnents/generic/GenericCardFooter.vue";

const code = ref(["*", "*", "*", "*"]);
const isLoading = ref(false);

const wait = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

const fetchCode = async () => {
  isLoading.value = true;
  code.value = ["*", "*", "*", "*"];

  try {
    await wait(5000);

    const response = await fetch(`https://mct-marty.be/happy-home/`);
    const data = await response.json();

    if (Array.isArray(data) && data.length >= 4) {
      code.value = data.slice(0, 4).map((d) => String(d));
    }
  } finally {
    isLoading.value = false;
  }
};

const handleGetNewCode = () => {
  fetchCode();
};
</script>

<style scoped>
main {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 0.75rem;
  background: #02007e;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
    sans-serif;
  padding: 1rem;
}

.app-header {
  display: flex;
  justify-content: center;
  width: 100%;
}

.app-header__home {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #ffffff;
}

.app-header__icon {
  width: 36px;
  height: 36px;
}

.app-header__title {
  font-size: 1.8rem;
  font-weight: 700;
}

.close-icon {
  width: 20px;
  height: 20px;
}
</style>
