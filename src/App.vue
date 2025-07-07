<script setup lang="ts">
import { ref } from 'vue'
import Header from './components/Header.vue'
import Home from './components/Home.vue'
import Information from './components/Information.vue'
import Gallery from './components/Gallery.vue'
import Contact from './components/Contact.vue'
import Auth from './components/Auth.vue'
import Footer from './components/Footer.vue'

const activeSection = ref('home')

const setActiveSection = (section: string) => {
  activeSection.value = section
}
</script>

<template>
  <div id="app">
    <Header :activeSection="activeSection" @setActiveSection="setActiveSection" />
    <main>
      <Home v-if="activeSection === 'home'" @setActiveSection="setActiveSection" />
      <Information v-if="activeSection === 'information'" />
      <Gallery v-if="activeSection === 'gallery'" />
      <Contact v-if="activeSection === 'contact'" />
      <Auth v-if="activeSection === 'auth'" />
    </main>
    <Footer @setActiveSection="setActiveSection" />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  line-height: 1.6;
  color: #182D4F;
  background-color: #ffffff;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  flex: 1;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.btn {
  display: inline-block;
  padding: 0.75rem 2rem;
  border: none;
  border-radius: 50px;
  font-weight: 600;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 1rem;
}

.btn-primary {
  background: linear-gradient(135deg, #A7105A, #d41a6b);
  color: white;
  border: 2px solid transparent;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(167, 16, 90, 0.3);
}

.btn-secondary {
  background: linear-gradient(135deg, #27C383, #2dd492);
  color: white;
  border: 2px solid transparent;
}

.btn-secondary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(39, 195, 131, 0.3);
}

.section-title {
  font-size: 3rem;
  font-weight: 700;
  color: #182D4F;
  text-align: center;
  margin-bottom: 3rem;
  position: relative;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 4px;
  background: linear-gradient(90deg, #A7105A, #27C383);
  border-radius: 2px;
}

@media (max-width: 768px) {
  .container {
    padding: 0 1rem;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>