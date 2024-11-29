<template>
  <section class="inline" :style="{ backgroundColor: backgroundColor }">
    <div
      class="inline-container"
      :class="{
        'reverse-layout': imagePosition === 'right',
      }"
    >
      <img v-if="image" :src="image" alt="What Is Image" class="inline-image" />
      <div class="inline-content">
        <h2 class="inline-header">{{ header }}</h2>
        <p v-if="text" class="inline-text">{{ text }}</p>
        <ul v-if="bulletList" class="inline-list">
          <li v-for="(item, index) in bulletList" :key="index">{{ item }}</li>
        </ul>
        <button v-if="buttonLabel" @click="buttonAction" class="inline-button">
          {{ buttonLabel }}
        </button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import type { PropType } from 'vue'

const props = defineProps({
  image: {
    type: String,
    default: null, // Optional, if no image is provided
  },
  imagePosition: {
    type: String as PropType<'left' | 'right'>,
    default: 'left', // Determines the position of the image
  },
  header: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    default: null, // Optional, if no text is provided
  },
  bulletList: {
    type: Array as PropType<string[]>,
    default: null, // Optional, if no bullet list is provided
  },
  buttonLabel: {
    type: String,
    default: null, // Optional, if no button is needed
  },
  buttonAction: {
    type: Function as PropType<() => void>,
    default: null, // Optional, if no button action is provided
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

.inline-container.reverse-layout {
  flex-direction: column-reverse;
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

.inline-list {
  margin: 1rem 0;
  padding-left: 1.5rem;
}

.inline-list li {
  margin-bottom: 0.5rem;
  line-height: 1.6;
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

  .inline-container.reverse-layout {
    flex-direction: row-reverse;
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
