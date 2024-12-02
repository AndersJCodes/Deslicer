<template>
  <article class="card-wrapper">
    <div class="card">
      <div class="card-header">
        <!-- Icon -->
        <div class="card-icon" v-if="icon">
          <img :src="icon" alt="Card Icon" />
        </div>

        <!-- Title -->
        <h3 class="card-title">{{ title }}</h3>
      </div>

      <!-- Paragraph -->
      <p class="card-paragraph">{{ paragraph }}</p>

      <!-- Features List -->
      <ul class="card-features" v-if="features.length > 0">
        <li v-for="(feature, index) in features" :key="index">
          <img v-if="feature.icon" :src="feature.icon" alt="Feature Icon" class="feature-icon" />
          {{ feature.text }}
        </li>
      </ul>

      <!-- Button -->
      <button v-if="buttonLabel" @click="buttonAction" class="card-button">
        {{ buttonLabel }}
      </button>
    </div>
  </article>
</template>

<script setup lang="ts">
interface Cardprops {
  icon?: string
  title: string
  paragraph: string
  features: Feature[]
  buttonLabel?: string
  buttonAction?: () => void
}

interface Feature {
  icon?: string
  text: string
}

withDefaults(defineProps<Cardprops>(), {
  icon: '',
  buttonLabel: '',
  features: () => [] as Feature[],
  buttonAction: () => {},
})
</script>

<style scoped>
/* Wrapper for gray background */
.card-wrapper {
  display: flex;
  gap: 1rem; /* Space between cards */
  justify-content: center; /* Center cards horizontally */
  align-items: stretch; /* Ensure cards have the same height */
  flex-wrap: wrap; /* Allow wrapping for responsiveness */
}

.card {
  display: flex;
  flex-direction: column; /* Stack content vertically */
  justify-content: space-between; /* Spread content evenly */
  background-color: var(--vt-c-white); /* White inner background */
  color: var(--vt-c-black-soft);
  border-radius: 16px;
  padding: 1rem;
  max-width: 350px;
  width: 100%;
  text-align: left; /* Left-align text */
}

.card-header {
  display: flex;
  align-items: center;
  gap: 0.5rem; /* Space between icon and title */
}
/* Icon Styling */
.card-icon img {
  width: 50px;
  height: 50px;
}

/* Title Styling */
.card-title {
  color: var(--vt-c-black-soft);
  font-size: 1.5rem;
  font-weight: bold;
}

/* Paragraph Styling */
.card-paragraph {
  /* font-size: 1rem; */
  color: var(--vt-c-black-soft);
  margin-bottom: 1.5rem;
}

/* Features List */
.card-features {
  list-style: none;
  padding: 0;
  margin: 0 0 1.5rem;
}

.card-features li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1.2rem;
}

.feature-icon {
  width: 20px;
  height: 20px;
}

/* Button Styling */
.card-button {
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  font-weight: bold;
  color: #f27405;
  background-color: transparent;
  border: 2px solid #f27405;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease-in-out;
}

.card-button:hover {
  background-color: #f97316;
}
</style>
