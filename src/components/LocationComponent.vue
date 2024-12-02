<template>
  <section class="location-section">
    <div class="location-container">
      <h2 class="location-title">Visit us</h2>
      <div class="location-card">
        <img :src="imageUrl" alt="Location Image" class="location-image" />
        <div class="location-info">
          <h3 class="card-title">{{ location }}</h3>
          <p class="location-address">
            Hornsgatan 156<br />
            117 28 Stockholm, Sweden<br />
            +46 12 345 67 89 <br />
            <a href="mailto:hej@deslicer.com">hej@deslicer.com</a>
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const props = defineProps({
  imageUrl: {
    type: String,
    required: true,
  },
  location: {
    type: String,
    required: true,
  },
})
</script>

<style scoped>
.location-section {
  padding: 6rem 2rem;
  background-color: #f8f8f8; /* Light gray */
  color: var(--vt-c-black);
}

.location-container {
  max-width: 1080px;
  margin: 0 auto;
  text-align: left;
}

.location-title {
  font-size: 1.8rem;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 1.5rem;
  padding-left: 2rem;
}

.location-card {
  /* background-color: #ffffff; */
  padding: 1.5rem;
  /* border-radius: 8px; */
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.location-image {
  width: 100%;
  height: auto;
  border-radius: 8px;
}

.location-info {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.card-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.location-address {
  font-size: 1rem;
  line-height: 1.6;
}

.location-address a {
  color: var(--vt-c-black);
}

/* Media query for desktop view */
@media (min-width: 768px) {
  .location-card {
    flex-direction: row; /* Arrange items in a row */
    align-items: end; /* Align items vertically */
  }

  .location-image {
    width: 50%; /* Adjust width for desktop view */
    margin-right: 1rem; /* Add space between image and text */
  }

  .location-info {
    width: 50%; /* Adjust width for desktop view */
  }
}
</style>
