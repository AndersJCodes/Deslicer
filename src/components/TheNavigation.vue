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
      <RouterLink class="logo" to="/" @click="closeMenu"
        ><img src="/deslicer_logo.png" alt="Company Logo" class="logo"
      /></RouterLink>
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
        <RouterLink to="/contact" @click="closeMenu" class="button">Contact</RouterLink>
      </nav>
    </div>
  </header>
</template>

<style scoped>
/* Add the provided CSS code here */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

/* General styles for mobile first */
.navbar {
  width: 100%;
  z-index: 10;
  max-width: 1080px;
  margin: 0 auto;
}

.nav-container {
  height: 62px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 2rem;
}

.logo {
  width: 150px;
  text-decoration: none;
  z-index: 10;
}

.menu-items {
  background-color: var(--vt-c-black);
  padding-top: 120px;
  height: 100vh;
  width: 100%;
  position: absolute;
  top: 0;
  right: 0;
  transform: translateY(-100%);
  opacity: 0;
  display: flex;
  flex-direction: column;
  padding-left: 2rem;
  transition: none;
  z-index: 5;
}

.menu-items a {
  text-decoration: none;
  font-size: 1.5rem;
  margin-bottom: 1.2rem;
}

.button {
  background-color: #f59e0b;
  border: none;
  border-radius: 100px;
  padding: 0.4rem 1rem;
  margin-right: 2rem;
}

.button:hover {
  background-color: #fbbf24;
}

.checkbox {
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

.hamburger-lines {
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
  cursor: pointer;
}

.hamburger-lines .line {
  height: 4px;
  width: 100%;
  border-radius: 10px;
  background: var(--color-text-dark-bg);
  transition: all 0.4s ease-in-out;
}

/* Checkbox interaction: Spin and shrink effect */
.checkbox:checked ~ .menu-items {
  transform: translateY(0);
  opacity: 1;
  transition:
    transform 0.5s ease-in-out,
    opacity 0.5s ease-in-out;
}

.checkbox:checked ~ .hamburger-lines .line1 {
  transform: rotate(45deg) translate(5px, 5px);
}

.checkbox:checked ~ .hamburger-lines .line2 {
  transform: scaleX(0);
  opacity: 0;
}

.checkbox:checked ~ .hamburger-lines .line3 {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* Hover animation for hamburger lines */
.hamburger-lines:hover .line {
  background-color: var(--vt-c-primary);
  transform: scaleX(1.1);
  transition: all 0.2s ease-in-out;
}

/* Media query for desktop */
@media (min-width: 768px) {
  .hamburger-lines,
  .checkbox {
    display: none; /* Hide hamburger menu */
  }

  .menu-items {
    position: static;
    transform: none;
    opacity: 1;
    background-color: transparent;
    flex-direction: row;
    align-items: center;
    height: auto;
    width: auto;
    padding-top: 0;
    padding-left: 0;
    transition: none;
  }

  .menu-items a {
    margin: 0 1rem;
    color: var(--color-text-dark-bg);
    font-size: 1rem;
  }

  .button {
    font-size: 1rem;
    padding: 0.4rem 1.2rem;
  }

  .button:hover {
    background-color: #fbbf24;
  }
}
</style>
