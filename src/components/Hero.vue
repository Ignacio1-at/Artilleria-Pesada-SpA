<script setup lang="ts">
import { ref, onMounted } from 'vue'

const particles = ref<Array<{ x: number; y: number; size: number; duration: number }>>([])

onMounted(() => {
  for (let i = 0; i < 15; i++) {
    particles.value.push({
      x: Math.random() * 100,
      y: Math.random() * 100,
      size: Math.random() * 4 + 2,
      duration: Math.random() * 10 + 10,
    })
  }
})

const images = [
  {
    url: '/MaquinaTitulo.jpeg',
    alt: 'Operaciones industriales',
  },
  {
    url: '/MaquinaTitulo2.jpeg',
    alt: 'Maquinaria pesada',
  },
  {
    url: '/Titulo3.jpeg',
    alt: 'Puerto y logística',
  },
]
</script>

<template>
  <section class="hero">
    <div class="hero-background">
      <div class="bg-image"></div>
      <div class="bg-gradient"></div>
      <div class="bg-pattern"></div>
    </div>

    <div class="particles">
      <div
        v-for="(particle, index) in particles"
        :key="index"
        class="particle"
        :style="{
          left: `${particle.x}%`,
          top: `${particle.y}%`,
          width: `${particle.size}px`,
          height: `${particle.size}px`,
          animationDuration: `${particle.duration}s`,
        }"
      ></div>
    </div>

    <div class="hero-container">
      <div class="hero-content">
        <div class="badge">EST. 2022</div>

        <h1 class="hero-title">
          <span class="title-pre">Somos</span>
          <div class="title-logo">
            <img src="/logo.png" alt="Artillería Pesada" class="main-logo" />
          </div>
          <div class="title-lema">
            <span class="lema-line"></span>
            <span class="lema-text"
              >"Trabajamos cada día para mover lo que el mundo necesita, con seguridad, precisión y
              excelencia."</span
            >
            <span class="lema-line"></span>
          </div>
        </h1>

        <p class="hero-description">
          Soluciones integrales en operación de maquinaria pesada, mantenimiento industrial y
          logística portuaria. Más de una década de experiencia respaldando los proyectos más
          importantes del país.
        </p>

        <div class="hero-actions">
          <a href="#contacto" class="cta-primary">
            <span>Solicitar Cotización</span>
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path
                d="M4 10H16M16 10L10 4M16 10L10 16"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
              />
            </svg>
          </a>
          <a href="#servicios" class="cta-secondary">
            <span>Ver Servicios</span>
          </a>
        </div>
      </div>

      <div class="hero-sidebar">
        <div class="photos-grid">
          <div v-for="(image, index) in images" :key="index" class="photo-item">
            <img :src="image.url" :alt="image.alt" />
            <div class="photo-overlay"></div>
          </div>
        </div>
      </div>
    </div>

    <div class="scroll-indicator">
      <span>DESLIZA</span>
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
        <path
          d="M12 5v14m0 0l7-7m-7 7l-7-7"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
        />
      </svg>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  padding: calc(var(--navbar-height) + 3rem) 3rem 3rem;
}

/* FONDO */
.hero-background {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.bg-image {
  position: absolute;
  inset: 0;
  background-image: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 800"><defs><pattern id="grid" width="40" height="40" patternUnits="userSpaceOnUse"><path d="M 40 0 L 0 0 0 40" fill="none" stroke="rgba(227,30,36,0.1)" stroke-width="1"/></pattern></defs><rect fill="%231a2842" width="1200" height="800"/><rect fill="url(%23grid)" width="1200" height="800"/></svg>');
  background-size: cover;
  background-position: center;
}

.bg-gradient {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    135deg,
    rgba(26, 40, 66, 0.95) 0%,
    rgba(44, 62, 95, 0.9) 50%,
    rgba(227, 30, 36, 0.2) 100%
  );
}

.bg-pattern {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(
      45deg,
      transparent 48%,
      rgba(227, 30, 36, 0.05) 49%,
      rgba(227, 30, 36, 0.05) 51%,
      transparent 52%
    ),
    linear-gradient(
      -45deg,
      transparent 48%,
      rgba(227, 30, 36, 0.05) 49%,
      rgba(227, 30, 36, 0.05) 51%,
      transparent 52%
    );
  background-size: 60px 60px;
  opacity: 0.5;
}

/* PARTÍCULAS */
.particles {
  position: absolute;
  inset: 0;
  overflow: hidden;
  z-index: 1;
}

.particle {
  position: absolute;
  background: var(--color-red);
  border-radius: 50%;
  opacity: 0.3;
  animation: float infinite ease-in-out;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0) translateX(0);
  }
  25% {
    transform: translateY(-20px) translateX(10px);
  }
  50% {
    transform: translateY(-40px) translateX(-10px);
  }
  75% {
    transform: translateY(-20px) translateX(5px);
  }
}

/* CONTENEDOR */
.hero-container {
  position: relative;
  z-index: 2;
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 4rem;
  align-items: center;
}

/* CONTENIDO */
.hero-content {
  color: var(--color-white);
}

.badge {
  display: inline-block;
  padding: 6px 18px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 4px;
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 2px;
  margin-bottom: 1.5rem;
  backdrop-filter: blur(10px);
}

.hero-title {
  display: flex;
  flex-direction: column;
  gap: 0.1rem;
  margin-bottom: 1.5rem;
}

.title-pre {
  font-size: 1.6rem;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.85);
  letter-spacing: 3px;
  text-transform: uppercase;
  margin-bottom: 0.75rem;
}

.title-logo {
  margin: 1rem 0 1.5rem 0;
  display: flex;
  justify-content: flex-start;
}

.main-logo {
  max-width: 320px;
  width: 100%;
  height: auto;
  filter: drop-shadow(0 0 40px rgba(227, 30, 36, 0.6)) drop-shadow(0 0 20px rgba(227, 30, 36, 0.4));
  transition: all 0.3s ease;
}

.main-logo:hover {
  transform: scale(1.05);
  filter: drop-shadow(0 0 40px rgba(227, 30, 36, 0.7));
}

/* SIDEBAR */
.hero-sidebar {
  display: flex;
  flex-direction: column;
  gap: 1.75rem;
}

.photos-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(25px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 16px;
  padding: 1.5rem;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
}

.photo-item {
  position: relative;
  aspect-ratio: 4/3;
  border-radius: 8px;
  overflow: hidden;
  transition: all 0.3s ease;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.photo-item:last-child {
  grid-column: 1 / -1;
  aspect-ratio: 16/9;
}

.photo-item:hover {
  transform: translateY(-5px);
  border-color: var(--color-red);
}

.photo-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.photo-item:hover img {
  transform: scale(1.05);
}

.photo-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.4) 0%, transparent 50%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.photo-item:hover .photo-overlay {
  opacity: 1;
}

/* LEMA */
.title-lema {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  margin-top: 0.5rem;
}

.lema-line {
  flex: 0.3;
  height: 2px;
  background: linear-gradient(to right, var(--color-red), transparent);
}

.lema-text {
  font-size: clamp(0.95rem, 2vw, 1.05rem);
  font-weight: 600;
  color: rgba(255, 255, 255, 1);
  letter-spacing: 0.3px;
  text-transform: none;
  white-space: normal;
  text-shadow: 0 2px 15px rgba(0, 0, 0, 0.5);
  max-width: 600px;
  line-height: 1.55;
  flex: 1;
  font-style: italic;
}

.hero-description {
  font-size: 1.05rem;
  line-height: 1.7;
  color: rgba(255, 255, 255, 0.85);
  max-width: 600px;
  margin-bottom: 2rem;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
}

/* BOTONES */
.hero-actions {
  display: flex;
  gap: 1.25rem;
}

.cta-primary,
.cta-secondary {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 14px 32px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1rem;
  border-radius: 6px;
  transition: all 0.3s ease;
}

.cta-primary {
  background: var(--color-red);
  color: var(--color-white);
  border: 2px solid var(--color-red);
}

.cta-primary:hover {
  transform: translateY(-2px);
  background: var(--color-red-dark);
  border-color: var(--color-red-dark);
}

.cta-primary svg {
  transition: transform 0.3s ease;
}

.cta-primary:hover svg {
  transform: translateX(4px);
}

.cta-secondary {
  background: transparent;
  border: 2px solid rgba(255, 255, 255, 0.3);
  color: var(--color-white);
}

.cta-secondary:hover {
  background: rgba(255, 255, 255, 0.1);
  border-color: var(--color-white);
  transform: translateY(-2px);
}

.photo-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.4) 0%, transparent 50%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.hero-photo-item:hover .photo-overlay {
  opacity: 1;
}

/* SCROLL INDICATOR */
.scroll-indicator {
  position: absolute;
  bottom: 2.5rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  color: rgba(255, 255, 255, 0.4);
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 3px;
  z-index: 2;
  animation: bounce 2s infinite;
}

@keyframes bounce {
  0%,
  100% {
    transform: translateX(-50%) translateY(0);
  }
  50% {
    transform: translateX(-50%) translateY(-10px);
  }
}

/* RESPONSIVE */
@media (max-width: 1200px) {
  .hero {
    padding: calc(var(--navbar-height) + 2rem) 2.5rem 2.5rem;
  }

  .hero-container {
    gap: 3rem;
  }

  .title-pre {
    font-size: 1.5rem;
  }

  .main-logo {
    max-width: 300px;
  }

  .photos-grid {
    padding: 1.5rem;
  }
}

@media (max-width: 1024px) {
  .hero {
    padding: calc(var(--navbar-height) + 2rem) 2rem 2rem;
  }

  .hero-container {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .hero-content {
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .title-pre {
    font-size: 1.4rem;
  }

  .title-logo {
    justify-content: center;
  }

  .main-logo {
    max-width: 280px;
  }

  .lema-line {
    flex: 0.2;
  }

  .hero-description {
    max-width: 100%;
  }

  .hero-sidebar {
    max-width: 550px;
    width: 100%;
    margin: 0 auto;
  }

  .photos-grid {
    padding: 1.5rem;
  }

  .title-lema {
    gap: 1.25rem;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: calc(var(--navbar-height) + 1.5rem) 1.5rem 2rem;
    min-height: auto;
  }

  .hero-container {
    gap: 2.5rem;
  }

  .badge {
    font-size: 0.7rem;
    padding: 6px 16px;
    margin-bottom: 1.25rem;
  }

  .title-pre {
    font-size: clamp(1.2rem, 4vw, 1.5rem);
    letter-spacing: 2px;
  }

  .title-logo {
    margin: 1.25rem 0 1.5rem 0;
    justify-content: center;
  }

  .main-logo {
    max-width: 280px;
  }

  .title-lema {
    flex-direction: column;
    gap: 1rem;
    margin-top: 1rem;
  }

  .lema-line {
    display: none;
  }

  .lema-text {
    font-size: clamp(0.9rem, 2.5vw, 1rem);
    white-space: normal;
    text-align: center;
    letter-spacing: 0.5px;
    line-height: 1.5;
  }

  .hero-description {
    font-size: clamp(0.95rem, 2.5vw, 1.05rem);
    line-height: 1.7;
    margin-bottom: 1.75rem;
  }

  .hero-actions {
    flex-direction: column;
    width: 100%;
    max-width: 400px;
    gap: 1rem;
  }

  .cta-primary,
  .cta-secondary {
    width: 100%;
    justify-content: center;
    padding: 14px 32px;
    font-size: 1rem;
  }

  .scroll-indicator {
    display: none;
  }

  .hero-sidebar {
    max-width: 100%;
  }

  .photos-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
    padding: 1.25rem;
  }

  .photo-item {
    aspect-ratio: 16/9;
  }

  .photo-item:last-child {
    grid-column: 1;
  }
}

@media (max-width: 480px) {
  .hero {
    padding: calc(var(--navbar-height) + 1rem) 1rem 1.5rem;
  }

  .hero-container {
    gap: 2rem;
  }

  .badge {
    font-size: 0.65rem;
    padding: 5px 14px;
    letter-spacing: 1.5px;
    margin-bottom: 1rem;
  }

  .title-pre {
    font-size: clamp(1rem, 4vw, 1.2rem);
  }

  .title-logo {
    margin: 1rem 0;
  }

  .main-logo {
    max-width: 240px;
  }

  .title-lema {
    margin-top: 1rem;
  }

  .lema-text {
    font-size: clamp(0.8rem, 2.5vw, 0.9rem);
    line-height: 1.5;
  }

  .hero-description {
    font-size: clamp(0.9rem, 2.5vw, 1rem);
    margin-bottom: 1.5rem;
    line-height: 1.6;
  }

  .hero-actions {
    max-width: 100%;
  }

  .cta-primary,
  .cta-secondary {
    padding: 12px 24px;
    font-size: clamp(0.9rem, 2.5vw, 0.95rem);
  }

  .photos-grid {
    gap: 0.75rem;
    padding: 1rem;
  }

  .photo-item {
    aspect-ratio: 16/9;
    border-radius: 6px;
  }
}
</style>
