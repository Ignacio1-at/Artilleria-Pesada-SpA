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
  background: #ffffff;
}

.bg-gradient {
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(255, 255, 255, 1) 0%, rgba(245, 247, 250, 1) 100%);
}

.bg-pattern {
  position: absolute;
  inset: 0;
  background-image: radial-gradient(rgba(26, 40, 66, 0.02) 1px, transparent 1px);
  background-size: 24px 24px;
  opacity: 1;
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
  background: var(--color-navy);
  border-radius: 50%;
  opacity: 0.08;
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
  color: var(--color-navy);
}

.badge {
  display: inline-block;
  padding: 6px 16px;
  background: rgba(26, 40, 66, 0.06);
  border: 1px solid rgba(26, 40, 66, 0.12);
  border-radius: 20px;
  color: var(--color-navy);
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 1.5px;
  margin-bottom: 1.5rem;
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
  justify-content: center;
}

.main-logo {
  max-width: 320px;
  width: 100%;
  height: auto;
  filter: drop-shadow(0 2px 12px rgba(0, 0, 0, 0.08));
  transition: all 0.3s ease;
}

.main-logo:hover {
  transform: scale(1.03);
  filter: drop-shadow(0 4px 20px rgba(0, 0, 0, 0.12));
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
  gap: 0.875rem;
  background: var(--color-white);
  border: 1px solid rgba(26, 40, 66, 0.08);
  border-radius: 12px;
  padding: 1.25rem;
  box-shadow: 0 4px 24px rgba(26, 40, 66, 0.06);
}

.photo-item {
  position: relative;
  aspect-ratio: 4/3;
  border-radius: 8px;
  overflow: hidden;
  transition: all 0.3s ease;
  border: 1px solid rgba(26, 40, 66, 0.06);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
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
  background: linear-gradient(90deg, var(--color-red) 0%, rgba(214, 0, 0, 0.2) 100%);
  border-radius: 1px;
}

.lema-text {
  font-size: clamp(0.9rem, 1.8vw, 1rem);
  font-weight: 500;
  color: var(--color-text-light);
  letter-spacing: 0.2px;
  text-transform: none;
  white-space: normal;
  max-width: 550px;
  line-height: 1.6;
  flex: 1;
  font-style: italic;
}

.hero-description {
  font-size: 1rem;
  line-height: 1.75;
  color: var(--color-text-light);
  max-width: 560px;
  margin-bottom: 2rem;
  font-weight: 400;
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
  padding: 12px 28px;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  border-radius: 8px;
  transition: all 0.25s ease;
}

.cta-primary {
  background: var(--color-red);
  color: var(--color-white);
  border: 1px solid var(--color-red);
  box-shadow: 0 2px 8px rgba(214, 0, 0, 0.2);
}

.cta-primary:hover {
  transform: translateY(-1px);
  background: var(--color-red-dark);
  border-color: var(--color-red-dark);
  box-shadow: 0 4px 12px rgba(214, 0, 0, 0.25);
}

.cta-primary svg {
  transition: transform 0.3s ease;
}

.cta-primary:hover svg {
  transform: translateX(4px);
}

.cta-secondary {
  background: transparent;
  border: 1px solid rgba(26, 40, 66, 0.2);
  color: var(--color-navy);
}

.cta-secondary:hover {
  background: rgba(26, 40, 66, 0.04);
  border-color: rgba(26, 40, 66, 0.3);
  transform: translateY(-1px);
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
  color: var(--color-text-light);
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 2px;
  z-index: 2;
  animation: bounce 2.5s infinite;
  opacity: 0.5;
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
