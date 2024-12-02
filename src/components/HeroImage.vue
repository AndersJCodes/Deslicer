<template>
  <div class="hero-container">
    <!-- Background Image -->
    <img :src="image" alt="Hero Background" class="hero-image" />

    <!-- Content Overlay -->
    <div class="hero-content">
      <p v-if="subHeader" class="sub-header">{{ subHeader }}</p>
      <h1>{{ header }}</h1>
      <p v-if="paragraph" class="hero-paragraph">{{ paragraph }}</p>
      <div class="hero-buttons">
        <button
          v-for="(button, index) in buttons"
          :key="index"
          :class="['hero-button', index === 0 ? 'primary' : 'secondary']"
          @click="button.action"
        >
          {{ button.label }}
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { withDefaults } from 'vue'

interface Button {
  label: string
  action: () => void
}

interface HeroImageProps {
  header: string
  image?: string
  buttons?: Button[]
  paragraph?: string
  subHeader?: string
}

//Define props with type annotations and default values
withDefaults(defineProps<HeroImageProps>(), {
  image: '',
  buttons: () => [] as Button[],
  paragraph: '',
  subHeader: '',
})
</script>

<style scoped>
.hero-container {
  position: relative;
  width: 100%;
  margin: 0;
}

.hero-image {
  position: absolute;
  top: -62px;
  left: 50%;
  width: 100vw;
  height: 38rem;
  object-fit: cover;
  transform: translateX(-50%);
  z-index: -10;
}

.hero-content {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: left;
  justify-content: end;
  height: 34rem;
  text-align: left;
  padding: 2rem;
  /* color: var(--vt-c-white); */
  max-width: 1080px;
  margin: 0 auto;
}

.sub-header {
  font-size: 0.8em;
  color: var(--vt-c-white-mute);
  font-weight: 200;
}

.hero-content h1 {
  color: var(--vt-c-white);
  font-size: 3.5rem;
  max-width: 600px;
  padding-bottom: 2rem;
}

.hero-paragraph {
  color: var(--vt-c-white-soft);
  margin-bottom: 1.5rem;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
}

.hero-button {
  padding: 1rem 1.5rem;
  /* font-size: 1rem; */
  font-weight: bold;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease-in-out;
}

.hero-button.primary {
  color: var(--vt-c-black-soft);
  background-color: var(--vt-c-white);
}

.hero-button.primary:hover {
  background-color: var(--vt-c-white-soft);
}

.hero-button.secondary {
  background-color: transparent;
  color: var(--vt-c-white);
  border: 2px solid var(--vt-c-white);
}

.hero-button.secondary:hover {
  background-color: var(--vt-c-black-soft);
}
</style>
