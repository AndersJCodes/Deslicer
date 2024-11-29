<template>
  <section class="header-section">
    <div class="header-content">
      <p v-if="subHeader" class="header-subheader">{{ subHeader }}</p>
      <h1 class="header-title">{{ header }}</h1>
      <p v-if="paragraph" class="header-paragraph">{{ paragraph }}</p>
    </div>
  </section>
</template>

<script setup lang="ts">
const props = defineProps({
  header: {
    type: String,
    required: true,
  },
  subHeader: {
    type: String,
    required: false,
  },
  paragraph: {
    type: String,
    required: false,
  },
})
</script>

<style scoped>
.header-section {
  background-color: #ffffff;
  text-align: left;
}

.header-content {
  max-width: 1080px;
  margin: 0 auto;
  padding: 2rem;
}

.header-subheader {
  font-size: 1.5rem;
  color: #2c3e50;
  margin-bottom: 0.5rem;
}

.header-title {
  font-size: 2.5rem;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.header-paragraph {
  font-size: 1rem;
  color: #2c3e50;
  line-height: 1.6;
}
</style>
