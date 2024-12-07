<!-- GitHub Copilot -->

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
        <button v-if="buttonLabel" @click="buttonAction" class="inline-button">
          {{ buttonLabel }}
        </button>
      </div>
    </div>
    <ul v-if="bulletList" class="inline-list">
      <li v-for="(item, index) in bulletList" :key="index">{{ item }}</li>
    </ul>
  </section>
</template>

<script setup lang="ts">
interface Props {
  image?: string
  imagePosition: 'left' | 'right'
  header: string
  text?: string
  bulletList?: string[]
  buttonLabel?: string
  buttonAction?: () => void
  backgroundColor: string
}

defineProps<Props>()
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
  padding: 6rem 2rem 0rem 2rem;
}

.inline-image {
  width: 100%;
  max-width: 600px;
  object-fit: cover;
  border-radius: 16px;
}

.inline-content {
  text-align: left;
  max-width: 600px; /* Adjusted to prevent excessive width */
  color: var(--vt-c-black-mute);
}

.inline-header {
  font-size: 2rem;
  color: var(--vt-c-black-mute);
  margin-bottom: 1rem;
}

.inline-text {
  /* font-size: 1rem; */
  /*  line-height: 1.6; */
  margin-bottom: 2rem;
}

.inline-list {
  color: var(--vt-c-black-mute);
  margin: 1rem 0;
  padding: 0 2rem 6rem 3rem;
  list-style-type: disc;
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
    justify-content: space-between;
  }

  .inline-container.reverse-layout {
    flex-direction: row-reverse;
  }

  .reverse-layout .form-info {
    margin-right: 0;
    margin-left: 2rem;
  }

  .inline-image {
    flex: 1;
    max-width: 50%;
  }

  .inline-content {
    flex: 1;
    text-align: left;
  }

  /* Adjust the section layout to stack bullet list below image */
  .inline {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  /* Ensure bullets take full width */
  .inline-list {
    display: flex;
    gap: 3rem;
    width: 100%;
    max-width: 1080px;
  }
}
</style>
