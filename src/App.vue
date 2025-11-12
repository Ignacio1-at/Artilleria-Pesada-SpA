<script setup lang="ts">
import { ref } from 'vue'
import NavBar from './components/NavBar.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Services from './components/Services.vue'
import Safety from './components/Safety.vue'
import Infrastructure from './components/Infrastructure.vue'
import Values from './components/Values.vue'
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
      <Safety id="seguridad" />
      <Infrastructure id="infraestructura" />
      <Values id="valores" />
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
