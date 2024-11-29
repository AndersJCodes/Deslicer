<template>
  <section class="inline" :style="{ backgroundColor: backgroundColor }">
    <div class="inline-container">
      <img :src="image" alt="What Is Image" class="inline-image" />
      <div class="inline-content">
        <h2 class="inline-header">{{ header }}</h2>
        <p class="inline-text">{{ text }}</p>
        <button @click="buttonAction" class="inline-button">{{ buttonLabel }}</button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import type { PropType } from 'vue'

const props = defineProps({
  image: {
    type: String,
    required: true,
  },
  header: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    required: true,
  },
  buttonLabel: {
    type: String,
    required: true,
  },
  buttonAction: {
    type: Function as PropType<() => void>,
    required: true,
  },
  backgroundColor: {
    type: String,
    default: '#e5e5e5', // Default light background color
  },
})
</script>

<style scoped>
.inline {
  width: 100%;
}

.inline-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 1080px;
  margin: 0 auto;
  gap: 2rem;
  padding: 6rem 2rem;
}

.inline-image {
  width: 100%;
  max-width: 600px;
  object-fit: cover;
  border-radius: 16px;
}

.inline-content {
  text-align: left;

  max-width: 1080px;
  color: var(--vt-c-black-mute);
}

.inline-header {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.inline-text {
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.inline-button {
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  font-weight: bold;
  color: #ffffff;
  background-color: #ea580c;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease-in-out;
}

.inline-button:hover {
  background-color: #f97316;
}

@media (min-width: 768px) {
  .inline-container {
    flex-direction: row;
    align-items: center;
  }

  .inline-image {
    flex: 1;
    max-width: 50%;
  }

  .inline-content {
    flex: 1;
    text-align: left;
  }
}
</style>
