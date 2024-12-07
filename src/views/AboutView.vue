<script setup lang="ts">
import AboutTeam from '@/components/TheTeam.vue'
import Chatbot from '@/components/ChatBot.vue'
import Hero from '@/components/TheHero.vue'
</script>

<template>
  <main>
    <Hero
      subHeader="Our Mission"
      header="SIEM management for humans"
      paragraph="Focus on analysis and growth, instead of onboardings, support and updates."
      image="./images/siem-automation-desclier-about-hero.jpg"
    />
    <AboutTeam />
    <Chatbot />
  </main>
</template>

<style></style>
