<template>
  <div class="container">
    <section class="container-content">
      <h2>Clients:</h2>
      <div class="logo-grid">
        <div v-for="(logo, index) in logos" :key="index" class="logo-item">
          <img :src="logo.src" :alt="logo.alt" />
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// Dummy logos
const logos = ref([
  { src: 'customerlogos/logoipsum-239.svg', alt: 'Logo 1' },
  { src: 'customerlogos/logoipsum-260.svg', alt: 'Logo 2' },
  { src: 'customerlogos/logoipsum-263.svg', alt: 'Logo 3' },
  { src: 'customerlogos/logoipsum-264.svg', alt: 'Logo 4' },
  { src: 'customerlogos/logoipsum-265.svg', alt: 'Logo 5' },
])
</script>

<style scoped>
.container {
  background-color: var(--vt-c-white-soft);
}

.container-content {
  max-width: 1080px;
  margin: 0 auto;
  padding: 2rem 2rem;
}

.container-content h2 {
  color: var(--vt-c-black-soft);
}

.logo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 1.5rem;
  padding: 2rem;
  transition: background-color 0.5s; /* Smooth transition for background */
}

.logo-item {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
}

.logo-item img {
  max-width: 100%;
  height: auto;
}

.logo-item:hover {
  transform: scale(1.05); /* Slight zoom on hover */
}
</style>
