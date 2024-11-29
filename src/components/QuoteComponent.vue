<template>
  <section class="quote-component">
    <div class="quote-content">
      <!-- Top Section -->
      <div class="quote-top">
        <h1 class="quote-header">{{ header }}</h1>
        <p class="quote-description">{{ description }}</p>
        <div class="quote-buttons">
          <button
            v-if="primaryButtonLabel"
            @click="primaryButtonAction"
            class="quote-button primary"
          >
            {{ primaryButtonLabel }}
          </button>
          <button
            v-if="secondaryButtonLabel"
            @click="secondaryButtonAction"
            class="quote-button secondary"
          >
            {{ secondaryButtonLabel }}
          </button>
        </div>
      </div>

      <!-- Quote Section -->
      <div class="quote-middle">
        <p class="quote-text">"{{ quote }}"</p>
        <p class="quote-name">
          <strong>{{ name }}</strong>
          <span class="quote-company">{{ company }}</span>
        </p>
      </div>

      <!-- Image Section -->
      <div class="quote-image-container" v-if="image">
        <img :src="image" alt="Quote Image" class="quote-image" />
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import type { PropType } from 'vue'

const props = defineProps({
  subHeader: {
    type: String,
  },
  header: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: false,
    default: '',
  },
  primaryButtonLabel: {
    type: String,
    required: false,
  },
  primaryButtonAction: {
    type: Function as PropType<() => void>,
    default: () => {},
  },
  secondaryButtonLabel: {
    type: String,
    required: false,
  },
  secondaryButtonAction: {
    type: Function as PropType<() => void>,
    default: () => {},
  },
  quote: {
    type: String,
    required: true,
  },
  name: {
    type: String,
    required: true,
  },
  company: {
    type: String,
    required: false,
    default: '',
  },
  image: {
    type: String,
    required: false,
  },
})
</script>

<style scoped>
.quote-component {
  background-color: #fff7ed; /* Light background */
}

.quote-content {
  padding: 6rem 2rem;
  border-radius: 12px;
  text-align: left;
  max-width: 1024px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.quote-top {
  text-align: left;
}

.quote-sub-header {
  font-size: 1rem;
  color: #2c3e50;
  font-weight: 500;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
}

.quote-header {
  font-size: 2.5rem;
  font-weight: bold;
  color: #181818;
  margin-bottom: 1rem;
}

.quote-description {
  font-size: 1rem;
  line-height: 1.6;
  color: #2c3e50;
  margin-bottom: 1.5rem;
}

.quote-buttons {
  display: flex;
  gap: 1rem;
}

.quote-button {
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  font-weight: bold;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

.quote-button.primary {
  background-color: var(--vt-c-black-mute); /* Dark button */
  color: white;
}

.quote-button.primary:hover {
  background-color: #1b2937;
}

.quote-button.secondary {
  background-color: transparent;
  color: #2c3e50;
  border: 2px solid #2c3e50;
}

.quote-button.secondary:hover {
  background-color: #f2f2f2;
}

.quote-middle {
  text-align: left;
}

.quote-text {
  font-size: 1.5rem;
  font-style: italic;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.quote-name {
  font-size: 1rem;
  color: #2c3e50;
}

.quote-company {
  font-size: 0.9rem;
  color: #6b6b6b;
  margin-left: 0.5rem;
}

.quote-image-container {
  display: flex;
  justify-content: center;
}

.quote-image {
  max-width: 100%;
  border-radius: 12px;
  object-fit: cover;
}
</style>
