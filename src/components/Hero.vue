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
          <span class="title-main">
            <span class="title-line">ARTILLERÍA PESADA</span>
            <span class="title-line">
              REPARACIÓN INDUSTRIAL <span class="spa-badge">SpA</span>
            </span>
          </span>
          <div class="title-lema">
            <span class="lema-line"></span>
            <span class="lema-text">La fuerza que mueve la industria chilena</span>
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
        <div class="logo-showcase">
          <img src="/logo.png" alt="Artillería Pesada" class="showcase-logo" />
        </div>

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
  padding: var(--navbar-height) 2rem 0;
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
  grid-template-columns: 1.4fr 1fr;
  gap: 5rem;
  align-items: center;
}

/* CONTENIDO */
.hero-content {
  color: var(--color-white);
}

.badge {
  display: inline-block;
  padding: 8px 20px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 4px;
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 2px;
  margin-bottom: 2rem;
  backdrop-filter: blur(10px);
}

.hero-title {
  display: flex;
  flex-direction: column;
  gap: 0.1rem;
  margin-bottom: 2rem;
}

.title-pre {
  font-size: 1.5rem;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.7);
  letter-spacing: 3px;
  text-transform: uppercase;
}

.title-main {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -2px;
  color: var(--color-white);
  text-shadow: 2px 2px 20px rgba(0, 0, 0, 0.5);
}

.title-line {
  font-size: clamp(2.5rem, 7vw, 4.5rem);
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}

.spa-badge {
  color: var(--color-red);
  font-size: clamp(1.8rem, 5vw, 3rem);
  font-weight: 700;
  padding: 0.25rem 0.75rem;
  border: 2px solid var(--color-red);
  border-radius: 6px;
}

.title-lema {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  margin-top: 1rem;
}

.lema-line {
  flex: 1;
  height: 2px;
  background: linear-gradient(to right, transparent, var(--color-red), transparent);
}

.lema-text {
  font-size: 1.35rem;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.95);
  letter-spacing: 0.5px;
  text-transform: uppercase;
  white-space: nowrap;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
}

.hero-description {
  font-size: 1.15rem;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.8);
  max-width: 650px;
  margin-bottom: 2.5rem;
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
  padding: 16px 38px;
  text-decoration: none;
  font-weight: 600;
  font-size: 1.05rem;
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

/* SIDEBAR */
.hero-sidebar {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.logo-showcase {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 3.5rem 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.showcase-logo {
  max-width: 200px;
  height: auto;
  filter: drop-shadow(0 0 20px rgba(227, 30, 36, 0.3));
  transition: transform 0.3s ease;
}

.logo-showcase:hover .showcase-logo {
  transform: scale(1.05);
}

.photos-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
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
  .hero-container {
    gap: 3rem;
  }

  .title-line {
    font-size: clamp(2rem, 6vw, 3.5rem);
  }

  .spa-badge {
    font-size: clamp(1.5rem, 4vw, 2.5rem);
  }
}

@media (max-width: 1024px) {
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

  .hero-description {
    max-width: 100%;
  }

  .hero-sidebar {
    max-width: 600px;
    margin: 0 auto;
    width: 100%;
  }

  .logo-showcase {
    padding: 2.5rem 2rem;
  }

  .showcase-logo {
    max-width: 180px;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: calc(var(--navbar-height) + 1rem) 1.5rem 2rem;
    min-height: auto;
  }

  .hero-container {
    gap: 2.5rem;
  }

  .badge {
    font-size: 0.7rem;
    padding: 6px 16px;
    margin-bottom: 1.5rem;
  }

  .title-pre {
    font-size: 1.1rem;
    letter-spacing: 2px;
  }

  .title-line {
    font-size: 2rem;
    letter-spacing: -1px;
  }

  .spa-badge {
    font-size: 1.4rem;
    padding: 0.2rem 0.6rem;
  }

  .title-lema {
    flex-direction: column;
    gap: 1rem;
    margin-top: 1.5rem;
  }

  .lema-line {
    display: none;
  }

  .lema-text {
    font-size: 0.95rem;
    white-space: normal;
    text-align: center;
    letter-spacing: 0.5px;
  }

  .hero-description {
    font-size: 1rem;
    line-height: 1.7;
    margin-bottom: 2rem;
  }

  .hero-actions {
    flex-direction: column;
    width: 100%;
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
    max-width: 500px;
  }

  .logo-showcase {
    padding: 2rem 1.5rem;
  }

  .showcase-logo {
    max-width: 160px;
  }

  .photos-grid {
    grid-template-columns: 1fr;
    gap: 0.75rem;
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
    padding: calc(var(--navbar-height) + 0.5rem) 1rem 1.5rem;
  }

  .hero-container {
    gap: 2rem;
  }

  .badge {
    font-size: 0.65rem;
    padding: 5px 14px;
    letter-spacing: 1.5px;
  }

  .title-pre {
    font-size: 1rem;
  }

  .title-line {
    font-size: 1.6rem;
    gap: 0.5rem;
  }

  .spa-badge {
    font-size: 1.1rem;
    padding: 0.15rem 0.5rem;
  }

  .lema-text {
    font-size: 0.85rem;
    line-height: 1.4;
  }

  .hero-description {
    font-size: 0.95rem;
    margin-bottom: 1.75rem;
  }

  .cta-primary,
  .cta-secondary {
    padding: 12px 28px;
    font-size: 0.95rem;
  }

  .logo-showcase {
    padding: 1.75rem 1.25rem;
  }

  .showcase-logo {
    max-width: 140px;
  }

  .photos-grid {
    gap: 0.6rem;
  }

  .photo-item {
    aspect-ratio: 16/9;
    border-radius: 6px;
  }
}
</style>
