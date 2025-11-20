<script setup lang="ts">
import { ref } from 'vue'
import NavBar from './components/NavBar.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Services from './components/Services.vue'
import ServiceDetails from './components/ServiceDetails.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

const activeSection = ref('inicio')
</script>

<template>
  <div class="app">
    <NavBar :active-section="activeSection" />
    <main>
      <Hero id="inicio" />
      <About id="nosotros" />
      <Services id="servicios" />
      <ServiceDetails id="servicios-detallados" />
      <Contact id="contacto" />
    </main>
    <Footer />
  </div>
</template>

<style>
@import './assets/styles.css';

.app {
  min-height: 100vh;
}
</style>
