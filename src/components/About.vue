<script setup lang="ts">
import { ref } from 'vue'

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
            <h3>Historia</h3>
            <div class="story-content">
              <p>
                <strong>Artillería Pesada Reparación Industrial SpA</strong> nace en Chile con una
                visión clara: ser un referente en la operación y mantenimiento de maquinaria pesada,
                aportando soluciones confiables y eficientes a la industria, la minería y la
                logística portuaria.
              </p>
              <p>
                Fundada por <strong>Ángelo Cisternas Muñoz</strong>, profesional con amplia
                experiencia en operaciones marítimas e industriales, la compañía surge de la
                convicción de que la excelencia operativa y la seguridad son el motor que impulsa el
                desarrollo sostenible de las grandes faenas del país.
              </p>
              <p>
                Con presencia en distintas regiones del país, participamos activamente en
                operaciones estratégicas de transferencia y porteo de carga, manipulación de
                contenedores y servicios logísticos especializados.
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
        <div class="quote-icon">
          <svg viewBox="0 0 24 24" fill="none">
            <path
              d="M3 21c3 0 7-1 7-8V5c0-1.25-.756-2.017-2-2H4c-1.25 0-2 .75-2 1.972V11c0 1.25.75 2 2 2 1 0 1 0 1 1v1c0 1-1 2-2 2s-1 .008-1 1.031V20c0 1 0 1 1 1z"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M15 21c3 0 7-1 7-8V5c0-1.25-.757-2.017-2-2h-4c-1.25 0-2 .75-2 1.972V11c0 1.25.75 2 2 2h.75c0 2.25.25 4-2.75 4v3c0 1 0 1 1 1z"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
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
  padding: 4rem 3rem;
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

.quote-icon {
  width: 80px;
  height: 80px;
  margin: 0 auto 2rem;
  position: relative;
  z-index: 1;
}

.quote-icon svg {
  width: 100%;
  height: 100%;
  color: var(--color-red);
  opacity: 0.5;
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
    padding: 3rem 2rem;
    margin-top: 3rem;
  }

  .quote-icon {
    width: 70px;
    height: 70px;
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
    padding: 2.5rem 1.5rem;
    border-radius: 16px;
  }

  .quote-icon {
    width: 60px;
    height: 60px;
    margin-bottom: 1.5rem;
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
