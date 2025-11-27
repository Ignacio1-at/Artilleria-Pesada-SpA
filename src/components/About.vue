<script setup lang="ts">
import { ref } from 'vue'

const teamPhotos = [
  '/DIA DEL TRABAJADOR 2025/WhatsApp Image 2025-04-30 at 09.37.54 (1).jpeg',
  '/DIA DEL TRABAJADOR 2025/WhatsApp Image 2025-04-30 at 09.37.56 (1).jpeg',
  '/DIA DEL TRABAJADOR 2025/WhatsApp Image 2025-04-30 at 09.37.57 (2).jpeg',
  '/DIA DEL TRABAJADOR 2025/WhatsApp Image 2025-04-30 at 09.37.59 (1).jpeg',
]

// Modal state
const modalOpen = ref(false)
const currentImageIndex = ref(0)

const openModal = (index: number) => {
  currentImageIndex.value = index
  modalOpen.value = true
  document.body.style.overflow = 'hidden'
}

const closeModal = () => {
  modalOpen.value = false
  document.body.style.overflow = ''
}

const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % teamPhotos.length
}

const prevImage = () => {
  currentImageIndex.value = (currentImageIndex.value - 1 + teamPhotos.length) % teamPhotos.length
}

const stats = [
  { number: '2022', label: 'Año de Fundación' },
  { number: '3+', label: 'Años en el Mercado' },
  { number: '99%', label: 'Continuidad Operacional' },
  { number: '0', label: 'Accidentes con Tiempo Perdido' },
]

const values = [
  {
    icon: 'shield',
    title: 'Seguridad ante todo',
    description:
      'La seguridad es nuestro principio intransable. Cada decisión y acción en terreno se basa en proteger la vida, la salud y el bienestar de las personas.',
  },
  {
    icon: 'excellence',
    title: 'Excelencia Operacional',
    description:
      'Ejecutamos con precisión, eficiencia y compromiso. Buscamos mejorar continuamente nuestros procesos para alcanzar los más altos estándares del sector.',
  },
  {
    icon: 'responsibility',
    title: 'Responsabilidad y Cumplimiento',
    description:
      'Cumplimos lo que prometemos. La transparencia, el orden y la responsabilidad guían nuestras relaciones con clientes, colaboradores y comunidades.',
  },
  {
    icon: 'team',
    title: 'Trabajo en Equipo',
    description:
      'Creemos que los mejores resultados se logran con colaboración, comunicación efectiva y liderazgo compartido en todos los niveles de la organización.',
  },
  {
    icon: 'innovation',
    title: 'Innovación y Mejora Continua',
    description:
      'Promovemos la adopción de nuevas tecnologías, métodos y herramientas que optimicen nuestros procesos y reduzcan los riesgos operativos y ambientales.',
  },
  {
    icon: 'environment',
    title: 'Compromiso con el Entorno',
    description:
      'Operamos de manera responsable con el medio ambiente y las comunidades donde trabajamos, respetando las normativas y promoviendo prácticas sostenibles.',
  },
]
</script>

<template>
  <section id="nosotros" class="about">
    <div class="container">
      <!-- Header Section -->
      <div class="section-header">
        <div class="header-badge">QUIÉNES SOMOS</div>
        <h2 class="section-title">Sobre Nosotros</h2>
        <div class="title-line"></div>
      </div>

      <!-- Main Content Grid -->
      <div class="about-grid">
        <!-- Story Column -->
        <div class="story-column">
          <div class="story-card">
            <div class="story-content">
              <p>
                En <strong>Artillería Pesada Reparación Industrial SpA</strong> somos especialistas
                en operaciones logísticas, carguío y manejo de maquinaria pesada para la industria
                minera, portuaria e industrial. Nuestro trabajo se basa en tres pilares esenciales:
                seguridad, precisión y continuidad operacional.
              </p>
              <p>
                Contamos con una flota moderna de equipos de alto rendimiento y un equipo humano
                altamente capacitado, preparado para ejecutar operaciones críticas de forma
                eficiente y segura. Cada servicio que entregamos incorpora estándares rigurosos de
                control, supervisión en terreno y trazabilidad operativa, asegurando resultados
                confiables y sostenibles.
              </p>
              <p>
                Hemos desarrollado operaciones de carguío, transferencia y movimiento de materiales
                a granel y contenedores, manteniendo indicadores sobresalientes de accidentabilidad
                cero y cumplimiento del 100% en nuestras faenas.
              </p>
              <p>
                En AP, trabajamos día a día para mover lo que el mundo necesita, con seguridad,
                precisión y excelencia.
              </p>
            </div>
          </div>
        </div>

        <!-- Stats Column -->
        <div class="stats-column">
          <div class="stats-grid">
            <div v-for="(stat, index) in stats" :key="index" class="stat-card">
              <div class="stat-icon">
                <div class="icon-circle"></div>
              </div>
              <div class="stat-number">{{ stat.number }}</div>
              <div class="stat-label">{{ stat.label }}</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Team Section -->
      <div class="team-section">
        <div class="team-header">
          <div class="header-line-red"></div>
          <h3 class="team-title">Nuestro Equipo</h3>
          <div class="header-line-red"></div>
        </div>
        <p class="team-description">
          El corazón de Artillería Pesada son las personas. Valoramos el compromiso, la dedicación y
          el espíritu de equipo de cada uno de nuestros colaboradores.
        </p>
        <div class="team-gallery">
          <div
            v-for="(foto, index) in teamPhotos"
            :key="index"
            class="team-photo"
            @click="openModal(index)"
          >
            <img :src="foto" :alt="`Equipo AP ${index + 1}`" loading="lazy" />
            <div class="photo-overlay">
              <svg viewBox="0 0 24 24" fill="none">
                <path
                  d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"
                  stroke="currentColor"
                  stroke-width="2"
                />
                <circle cx="12" cy="12" r="3" stroke="currentColor" stroke-width="2" />
              </svg>
            </div>
          </div>
        </div>
      </div>

      <!-- Team Photo Modal -->
      <Transition name="modal">
        <div v-if="modalOpen" class="modal" @click="closeModal">
          <button class="modal-close" @click="closeModal">
            <svg viewBox="0 0 24 24" fill="none">
              <line x1="18" y1="6" x2="6" y2="18" stroke="currentColor" stroke-width="2" />
              <line x1="6" y1="6" x2="18" y2="18" stroke="currentColor" stroke-width="2" />
            </svg>
          </button>

          <div class="modal-content" @click.stop>
            <button class="modal-nav prev" @click="prevImage">
              <svg viewBox="0 0 24 24" fill="none">
                <polyline points="15 18 9 12 15 6" stroke="currentColor" stroke-width="3" />
              </svg>
            </button>

            <img :src="teamPhotos[currentImageIndex]" :alt="`Imagen ${currentImageIndex + 1}`" />

            <button class="modal-nav next" @click="nextImage">
              <svg viewBox="0 0 24 24" fill="none">
                <polyline points="9 18 15 12 9 6" stroke="currentColor" stroke-width="3" />
              </svg>
            </button>

            <div class="modal-counter">{{ currentImageIndex + 1 }} / {{ teamPhotos.length }}</div>
          </div>
        </div>
      </Transition>

      <!-- Values Section -->
      <div class="values-section-header">
        <div class="header-line-red"></div>
        <h3 class="values-title">Nuestros Valores Corporativos</h3>
        <div class="header-line-red"></div>
      </div>

      <div class="values-grid">
        <div v-for="(value, index) in values" :key="index" class="value-card">
          <!-- Icons -->
          <div class="value-icon-wrapper">
            <!-- Shield Icon -->
            <svg v-if="value.icon === 'shield'" class="value-icon" viewBox="0 0 24 24" fill="none">
              <path
                d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>

            <!-- Excellence Icon -->
            <svg
              v-if="value.icon === 'excellence'"
              class="value-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <polygon
                points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>

            <!-- Responsibility Icon -->
            <svg
              v-if="value.icon === 'responsibility'"
              class="value-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <path
                d="M9 11a3 3 0 1 0 6 0a3 3 0 0 0 -6 0"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
              />
              <path
                d="M12.02 21.5c1.92 -1.2 5.98 -3.01 5.98 -7.5a6 6 0 1 0 -12 0c0 4.5 4.06 6.3 5.98 7.5"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
              />
            </svg>

            <!-- Team Icon -->
            <svg v-if="value.icon === 'team'" class="value-icon" viewBox="0 0 24 24" fill="none">
              <path
                d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <circle
                cx="9"
                cy="7"
                r="4"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M23 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>

            <!-- Innovation Icon -->
            <svg
              v-if="value.icon === 'innovation'"
              class="value-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <path
                d="M9 18h6M10 22h4M15 7.5a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M12 10.5v.5m-3.5-.5-.5 6.5h8l-.5-6.5"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>

            <!-- Environment Icon -->
            <svg
              v-if="value.icon === 'environment'"
              class="value-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <path
                d="M12 22c5.523 0 10-4.477 10-10S17.523 2 12 2 2 6.477 2 12s4.477 10 10 10z"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <path
                d="M2 12h20M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </div>

          <h4>{{ value.title }}</h4>
          <p>{{ value.description }}</p>
        </div>
      </div>

      <!-- Quote Section -->
      <div class="quote-section">
        <p class="quote-text">
          Cada proyecto que emprendemos refleja nuestra filosofía: movemos lo que el mundo necesita,
          con la fuerza, precisión y confianza que caracteriza a nuestro equipo.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 6rem 0;
  background: linear-gradient(180deg, #f8f9fa 0%, #ffffff 100%);
  scroll-margin-top: var(--navbar-height);
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* HEADER */
.section-header {
  text-align: center;
  margin-bottom: 5rem;
}

.header-badge {
  display: inline-block;
  padding: 6px 18px;
  background: rgba(227, 30, 36, 0.1);
  border: 1px solid rgba(227, 30, 36, 0.3);
  border-radius: 20px;
  color: var(--color-red);
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 2px;
  margin-bottom: 1rem;
}

.section-title {
  font-size: clamp(2.5rem, 5vw, 3.5rem);
  color: var(--color-navy);
  font-weight: 900;
  margin-bottom: 1.5rem;
  letter-spacing: -1px;
}

.title-line {
  width: 80px;
  height: 4px;
  background: var(--color-red);
  margin: 0 auto;
}

/* MAIN GRID */
.about-grid {
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 4rem;
  margin-bottom: 5rem;
}

/* STORY COLUMN */
.story-column {
  display: flex;
  flex-direction: column;
}

.story-card {
  background: var(--color-white);
  padding: 3rem;
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  border-left: 4px solid var(--color-red);
  height: 100%;
}

.story-card h3 {
  color: var(--color-navy);
  font-size: 2rem;
  font-weight: 800;
  margin-bottom: 2rem;
  letter-spacing: -0.5px;
}

.story-content p {
  margin-bottom: 1.5rem;
  line-height: 1.8;
  color: var(--color-text);
  font-size: 1.05rem;
}

.story-content p:last-child {
  margin-bottom: 0;
}

.story-content strong {
  color: var(--color-navy);
  font-weight: 700;
}

/* STATS COLUMN */
.stats-column {
  display: flex;
  align-items: center;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
  width: 100%;
}

.stat-card {
  background: var(--color-white);
  padding: 2rem 1.5rem;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.06);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.stat-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, var(--color-red) 0%, var(--color-navy) 100%);
  transform: scaleX(0);
  transition: transform 0.3s ease;
}

.stat-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.12);
}

.stat-card:hover::before {
  transform: scaleX(1);
}

.stat-icon {
  width: 50px;
  height: 50px;
  margin: 0 auto 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.icon-circle {
  width: 12px;
  height: 12px;
  background: var(--color-red);
  border-radius: 50%;
  box-shadow: 0 0 0 8px rgba(227, 30, 36, 0.2);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 900;
  color: var(--color-navy);
  line-height: 1;
  margin-bottom: 0.75rem;
}

.stat-label {
  font-size: 0.9rem;
  color: var(--color-text);
  font-weight: 600;
  line-height: 1.4;
}

/* IDENTITY SECTION */
.identity-section {
  background: var(--color-navy);
  padding: 4rem 3rem;
  border-radius: 20px;
  color: var(--color-white);
  position: relative;
  overflow: hidden;
}

.identity-section::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(227, 30, 36, 0.15) 0%, transparent 70%);
  border-radius: 50%;
  transform: translate(30%, -30%);
}

.identity-header {
  text-align: center;
  margin-bottom: 3rem;
  position: relative;
  z-index: 1;
}

.identity-header h3 {
  font-size: 2rem;
  font-weight: 800;
  margin-bottom: 0.75rem;
  letter-spacing: -0.5px;
}

.identity-header p {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.7);
  font-weight: 500;
}

.identity-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  position: relative;
  z-index: 1;
}

.identity-card {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(10px);
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
}

.identity-card:hover {
  background: rgba(255, 255, 255, 0.12);
  border-color: var(--color-red);
  transform: translateY(-5px);
}

.identity-title {
  color: var(--color-red);
  font-size: 0.85rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1.5px;
  margin-bottom: 0.75rem;
}

.identity-value {
  font-size: 1.05rem;
  font-weight: 600;
  line-height: 1.5;
  color: var(--color-white);
}

/* VALUES SECTION */
.values-section-header {
  display: flex;
  align-items: center;
  gap: 2rem;
  margin: 5rem 0 4rem;
  justify-content: center;
}

/* TEAM SECTION */
.team-section {
  margin: 5rem 0;
  padding: 3rem;
  background: var(--color-white);
  border-radius: 20px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}

.team-header {
  display: flex;
  align-items: center;
  gap: 2rem;
  margin-bottom: 1.5rem;
  justify-content: center;
}

.team-title {
  font-size: 2rem;
  color: var(--color-navy);
  font-weight: 800;
  letter-spacing: -0.5px;
  text-align: center;
  margin: 0;
}

.team-description {
  text-align: center;
  color: var(--color-text);
  font-size: 1.1rem;
  line-height: 1.7;
  max-width: 700px;
  margin: 0 auto 2.5rem;
}

.team-gallery {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1.5rem;
}

.team-photo {
  position: relative;
  aspect-ratio: 1;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
}

.team-photo:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 30px rgba(227, 30, 36, 0.2);
}

.team-photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
}

.team-photo:hover img {
  transform: scale(1.1);
}

.photo-overlay {
  position: absolute;
  inset: 0;
  background: rgba(227, 30, 36, 0.85);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.team-photo:hover .photo-overlay {
  opacity: 1;
}

.photo-overlay svg {
  width: 48px;
  height: 48px;
  stroke: white;
}

/* Modal */
.modal {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.95);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;
  padding: 20px;
}

.modal-content {
  position: relative;
  max-width: 90vw;
  max-height: 90vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-content img {
  max-width: 100%;
  max-height: 90vh;
  object-fit: contain;
  border-radius: 12px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
}

.modal-close {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 50px;
  height: 50px;
  background: rgba(255, 255, 255, 0.1);
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  z-index: 10;
}

.modal-close:hover {
  background: var(--color-red);
  border-color: var(--color-red);
  transform: rotate(90deg);
}

.modal-close svg {
  width: 24px;
  height: 24px;
  stroke: white;
}

.modal-nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 60px;
  height: 60px;
  background: rgba(255, 255, 255, 0.1);
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  z-index: 10;
}

.modal-nav:hover {
  background: var(--color-red);
  border-color: var(--color-red);
  transform: translateY(-50%) scale(1.1);
}

.modal-nav svg {
  width: 28px;
  height: 28px;
  stroke: white;
}

.modal-nav.prev {
  left: 30px;
}

.modal-nav.next {
  right: 30px;
}

.modal-counter {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  padding: 12px 24px;
  background: rgba(255, 255, 255, 0.1);
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 30px;
  color: white;
  font-weight: 600;
  font-size: 1rem;
  backdrop-filter: blur(10px);
}

/* Modal Animations */
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

.header-line-red {
  flex: 1;
  max-width: 200px;
  height: 2px;
  background: linear-gradient(to right, transparent, var(--color-red), transparent);
}

.values-title {
  font-size: 2rem;
  color: var(--color-navy);
  font-weight: 800;
  letter-spacing: -0.5px;
  text-align: center;
  margin: 0;
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.value-card {
  background: var(--color-white);
  padding: 2.5rem 2rem;
  border-radius: 16px;
  text-align: center;
  transition: all 0.3s ease;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  position: relative;
  overflow: hidden;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.value-card::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: var(--color-red);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.value-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.value-card:hover::before {
  transform: scaleX(1);
}

.value-icon-wrapper {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, rgba(227, 30, 36, 0.1) 0%, rgba(26, 40, 66, 0.05) 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  transition: all 0.3s ease;
}

.value-icon {
  width: 40px;
  height: 40px;
  color: var(--color-red);
  transition: all 0.3s ease;
}

.value-card:hover .value-icon-wrapper {
  background: var(--color-red);
  transform: scale(1.1);
}

.value-card:hover .value-icon {
  color: var(--color-white);
  transform: scale(1.15);
}

.value-card h4 {
  color: var(--color-navy);
  font-size: 1.25rem;
  font-weight: 800;
  margin-bottom: 1rem;
  letter-spacing: -0.5px;
}

.value-card p {
  color: var(--color-text);
  line-height: 1.7;
  font-size: 0.95rem;
}

/* QUOTE SECTION */
.quote-section {
  background: var(--color-navy);
  padding: 2.5rem 3rem;
  border-radius: 20px;
  text-align: center;
  position: relative;
  color: var(--color-white);
  overflow: hidden;
  margin-top: 4rem;
}

.quote-section::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(227, 30, 36, 0.15) 0%, transparent 70%);
  border-radius: 50%;
  transform: translate(30%, -30%);
}

.quote-text {
  font-size: 1.5rem;
  font-style: italic;
  line-height: 1.8;
  max-width: 900px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
  font-weight: 500;
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .values-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .team-gallery {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .about {
    padding: 4rem 0;
  }

  .container {
    padding: 0 1.5rem;
  }

  .section-header {
    margin-bottom: 3rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .about-grid {
    gap: 2.5rem;
    margin-bottom: 3rem;
  }

  .story-card {
    padding: 2rem;
  }

  .story-card h3 {
    font-size: 1.6rem;
  }

  .story-content p {
    font-size: 1rem;
  }

  .stats-grid {
    grid-template-columns: 1fr;
    gap: 1.25rem;
  }

  .stat-number {
    font-size: 2.2rem;
  }

  .stat-label {
    font-size: 0.85rem;
  }

  .values-section-header {
    flex-direction: column;
    gap: 1rem;
    margin: 3rem 0 2.5rem;
  }

  .header-line-red {
    display: none;
  }

  .values-title {
    font-size: 1.6rem;
  }

  .values-grid {
    grid-template-columns: 1fr;
    gap: 1.75rem;
  }

  .team-section {
    padding: 2rem;
    margin: 3rem 0;
  }

  .team-header {
    flex-direction: column;
    gap: 1rem;
  }

  .team-title {
    font-size: 1.6rem;
  }

  .team-description {
    font-size: 1rem;
  }

  .team-gallery {
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }

  .value-card {
    padding: 2rem 1.75rem;
  }

  .value-icon-wrapper {
    width: 70px;
    height: 70px;
  }

  .value-icon {
    width: 35px;
    height: 35px;
  }

  .value-card h4 {
    font-size: 1.2rem;
  }

  .value-card p {
    font-size: 0.9rem;
  }

  .quote-section {
    padding: 2rem 2rem;
    margin-top: 3rem;
  }

  .quote-text {
    font-size: 1.2rem;
  }

  .identity-section {
    padding: 3rem 2rem;
    border-radius: 16px;
  }

  .identity-header h3 {
    font-size: 1.6rem;
  }

  .identity-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .identity-card {
    padding: 1.5rem;
  }
}

@media (max-width: 480px) {
  .about {
    padding: 3rem 0;
  }

  .container {
    padding: 0 1rem;
  }

  .header-badge {
    font-size: 0.7rem;
    padding: 5px 14px;
  }

  .section-title {
    font-size: 1.8rem;
  }

  .story-card {
    padding: 1.5rem;
  }

  .story-card h3 {
    font-size: 1.4rem;
    margin-bottom: 1.5rem;
  }

  .story-content p {
    font-size: 0.95rem;
    margin-bottom: 1.25rem;
  }

  .stat-card {
    padding: 1.5rem 1rem;
  }

  .stat-number {
    font-size: 2rem;
  }

  .stat-label {
    font-size: 0.8rem;
  }

  .values-title {
    font-size: 1.4rem;
  }

  .team-section {
    padding: 1.5rem;
  }

  .team-title {
    font-size: 1.4rem;
  }

  .team-description {
    font-size: 0.95rem;
    margin-bottom: 2rem;
  }

  .team-gallery {
    grid-template-columns: repeat(2, 1fr);
    gap: 0.75rem;
  }

  .team-photo {
    border-radius: 12px;
  }

  .photo-overlay svg {
    width: 36px;
    height: 36px;
  }

  .modal-nav {
    width: 48px;
    height: 48px;
  }

  .modal-nav.prev {
    left: 10px;
  }

  .modal-nav.next {
    right: 10px;
  }

  .modal-close {
    top: 10px;
    right: 10px;
    width: 44px;
    height: 44px;
  }

  .value-card {
    padding: 1.75rem 1.5rem;
  }

  .value-icon-wrapper {
    width: 65px;
    height: 65px;
  }

  .value-icon {
    width: 32px;
    height: 32px;
  }

  .value-card h4 {
    font-size: 1.1rem;
  }

  .value-card p {
    font-size: 0.9rem;
  }

  .quote-section {
    padding: 2rem 1.5rem;
    border-radius: 16px;
  }

  .quote-text {
    font-size: 1rem;
    line-height: 1.6;
  }

  .identity-section {
    padding: 2.5rem 1.5rem;
  }

  .identity-header {
    margin-bottom: 2rem;
  }

  .identity-header h3 {
    font-size: 1.4rem;
  }

  .identity-header p {
    font-size: 0.9rem;
  }

  .identity-card {
    padding: 1.25rem;
  }

  .identity-title {
    font-size: 0.75rem;
  }

  .identity-value {
    font-size: 0.95rem;
  }
}
</style>
