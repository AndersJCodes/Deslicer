<script setup lang="ts">
import { RouterLink } from 'vue-router'

const closeMenu = () => {
  const checkbox = document.getElementById('menu-toggle') as HTMLInputElement
  if (checkbox) checkbox.checked = false
}
</script>

<template>
  <header class="navbar">
    <div class="nav-container">
      <!-- Logo -->
      <RouterLink class="logo" to="/" @click="closeMenu">Deslicer</RouterLink>
      <!-- Hamburger Checkbox -->
      <input class="checkbox" type="checkbox" id="menu-toggle" />
      <!-- Hamburger Lines -->
      <div class="hamburger-lines">
        <span class="line line1"></span>
        <span class="line line2"></span>
        <span class="line line3"></span>
      </div>
      <!-- Menu Items -->
      <nav class="menu-items">
        <RouterLink to="/about" @click="closeMenu">About</RouterLink>
        <RouterLink to="/contact" @click="closeMenu">Contact</RouterLink>
      </nav>
    </div>
  </header>
</template>

<style scoped>
/* Add the provided CSS code here */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

.navbar {
  width: 100%;
  /* box-shadow: 0 1px 4px rgb(146 161 176 / 15%); */
  z-index: 10;
  max-width: 1080px;
  margin: 0 auto;
}

.nav-container {
  height: 62px;
}

.logo {
  position: absolute;
  top: 50%;
  left: 2rem;
  transform: translateY(-50%);
  font-size: 1.2rem;
  color: var(--color-text-dark-bg);
  z-index: 15;
}

.navbar .menu-items {
  display: flex;
}

.navbar .nav-container a {
  text-decoration: none;
  font-weight: 500;
  font-size: 1.2rem;
}

.navbar .nav-container a:hover {
  font-weight: bolder;
}

.nav-container {
  display: block;
  position: relative;
  height: 60px;
}

.nav-container .checkbox {
  position: absolute;
  display: block;
  height: 32px;
  width: 32px;
  top: 17px;
  right: 2rem;
  z-index: 12;
  opacity: 0;
  cursor: pointer;
}

.nav-container .hamburger-lines {
  display: block;
  height: 26px;
  width: 32px;
  position: absolute;
  top: 17px;
  right: 2rem;
  z-index: 10;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.nav-container .hamburger-lines .line {
  display: block;
  height: 4px;
  width: 100%;
  border-radius: 10px;
  background: var(--color-text-dark-bg);
}

.nav-container .hamburger-lines .line1 {
  transform-origin: 0% 0%;
  transition: transform 0.4s ease-in-out;
}

.nav-container .hamburger-lines .line2 {
  transition: transform 0.2s ease-in-out;
}

.nav-container .hamburger-lines .line3 {
  transform-origin: 0% 100%;
  transition: transform 0.4s ease-in-out;
}

.navbar .menu-items {
  background-color: var(--vt-c-black); /* TODO: Change to variables */
  padding-top: 120px;
  height: 100vh;
  width: 100%;
  position: absolute; /* Ensure it stays in place */
  top: 0;
  right: 0;
  transform: translateY(-100%); /* Initially slide out of view above */
  opacity: 0;
  display: flex;
  flex-direction: column;
  padding-left: 2rem;
  transition: transform 0.5s ease-in-out; /* Smooth transition for slide-in effect */
  text-align: left;
  z-index: 5; /* Ensure it overlays other elements */
}

.nav-container input[type='checkbox']:checked ~ .menu-items {
  transform: translateY(0);
  opacity: 1;
}

.nav-container input[type='checkbox']:checked ~ .hamburger-lines .line1 {
  transform: rotate(45deg);
}

.nav-container input[type='checkbox']:checked ~ .hamburger-lines .line2 {
  transform: scaleY(0);
}

.nav-container input[type='checkbox']:checked ~ .hamburger-lines .line3 {
  transform: rotate(-45deg);
}

.nav-container input[type='checkbox']:checked ~ .logo {
  display: none;
}
</style>
