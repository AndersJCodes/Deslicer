<script setup lang="ts">
const socialLinks = [
  { name: 'LinkedIn', href: 'https://linkedin.com', icon: 'svg/linkedin.svg' },
  { name: 'Twitter', href: 'https://twitter.com', icon: 'svg/x-social-media-white.svg' },
]
</script>

<template>
  <footer class="footer">
    <div class="footer-container">
      <!-- Branding Section -->
      <div class="footer-branding">
        <img src="/logo_icon_deslicer_white.jpg" alt="Company Logo" class="footer-logo" />
        <p class="footer-tagline">Accelerate SIEM data integration with AI</p>
      </div>
      <!-- Social Media -->
      <div class="footer-social">
        <a v-for="(social, index) in socialLinks" :key="index" :href="social.href" target="_blank">
          <img :src="social.icon" :alt="social.name" />
        </a>
      </div>
    </div>

    <!-- Legal Section -->
    <div class="footer-legal">
      <p>&copy; 2024 Deslicer. All rights reserved.</p>
      <a href="#privacy">Privacy Policy</a> | <a href="#terms">Terms of Service</a>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #000000; /* Black background */
  color: #ffffff; /* White text for contrast */
  padding: 4rem 2rem 4rem 2rem;
  text-align: center;
}

.footer-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 2rem;
  max-width: 1080px;
  margin: 0 auto;
}

.footer-branding {
  /* flex: 1; */
  text-align: left;
}

.footer-logo {
  max-width: 30px;
  margin-bottom: 1rem;
}

.footer-tagline {
  font-size: 1rem;
  color: #aaaaaa; /* Light gray for a softer tone */
}

.footer-contact {
  /* flex: 1; */
  text-align: left;
}

.footer-contact a {
  color: #f97316; /* Accent color for links */
  text-decoration: none;
}

.footer-social a {
  margin: 0 0.5rem;
  /* display: inline-block; */
}

.footer-social img {
  width: 24px;
  height: 24px;
}

.footer-legal {
  margin-top: 2rem;
  border-top: 1px solid #444444;
  padding-top: 1rem;
  font-size: 0.9rem;
  color: #aaaaaa; /* Light gray for legal text */
}

.footer-legal a {
  color: #ffffff;
  text-decoration: none;
}
</style>
