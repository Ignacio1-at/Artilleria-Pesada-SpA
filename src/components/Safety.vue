<script setup lang="ts">
const safetyPillars = [
  {
    icon: 'team',
    title: 'Cultura Preventiva',
    description:
      'Promovemos una cultura basada en la responsabilidad individual y colectiva, con liderazgo visible en todos los niveles.',
  },
  {
    icon: 'system',
    title: 'Sistema Integrado SSOMA',
    description:
      'Gestión integrada de Seguridad, Salud Ocupacional y Medio Ambiente con procedimientos documentados.',
  },
  {
    icon: 'compliance',
    title: 'Cumplimiento Normativo',
    description:
      'Operaciones bajo cumplimiento estricto de la normativa nacional vigente y lineamientos HSEC.',
  },
  {
    icon: 'target',
    title: 'Cero Daño',
    description:
      'Meta clara: cero accidentes, cero incidentes y cero impactos. Mejora continua en todos los procesos.',
  },
]

const stats = [
  { value: '0%', label: 'Accidentabilidad' },
  { value: '100%', label: 'Cumplimiento' },
  { value: '24/7', label: 'Supervisión' },
]
</script>

<template>
  <section id="seguridad" class="safety">
    <div class="container">
      <!-- Header -->
      <div class="section-header">
        <div class="header-badge">SEGURIDAD Y SALUD</div>
        <h2 class="section-title">Gestión de Seguridad y Salud Ocupacional</h2>
        <div class="title-line"></div>
        <p class="section-subtitle">
          La seguridad no es un requisito: es un valor esencial que guía cada una de nuestras
          operaciones
        </p>
      </div>

      <!-- Safety Pillars Grid -->
      <div class="safety-grid">
        <div v-for="(pillar, index) in safetyPillars" :key="index" class="safety-card">
          <!-- Icon -->
          <div class="safety-icon-wrapper">
            <!-- Team Icon -->
            <svg v-if="pillar.icon === 'team'" class="safety-icon" viewBox="0 0 24 24" fill="none">
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

            <!-- System Icon -->
            <svg
              v-if="pillar.icon === 'system'"
              class="safety-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <path
                d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <polyline
                points="14 2 14 8 20 8"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <line
                x1="9"
                y1="15"
                x2="15"
                y2="15"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <line
                x1="9"
                y1="11"
                x2="15"
                y2="11"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>

            <!-- Compliance Icon -->
            <svg
              v-if="pillar.icon === 'compliance'"
              class="safety-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <line
                x1="12"
                y1="20"
                x2="12"
                y2="10"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
              />
              <line
                x1="18"
                y1="20"
                x2="18"
                y2="4"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
              />
              <line
                x1="6"
                y1="20"
                x2="6"
                y2="16"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
              />
            </svg>

            <!-- Target Icon -->
            <svg
              v-if="pillar.icon === 'target'"
              class="safety-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <circle
                cx="12"
                cy="12"
                r="10"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <circle
                cx="12"
                cy="12"
                r="6"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <circle
                cx="12"
                cy="12"
                r="2"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </div>

          <!-- Content -->
          <h3>{{ pillar.title }}</h3>
          <p>{{ pillar.description }}</p>
        </div>
      </div>

      <!-- Commitment Section -->
      <div class="commitment-section">
        <div class="commitment-content">
          <div class="commitment-header">
            <div class="header-line-red"></div>
            <h3>Nuestro Compromiso con las Personas</h3>
          </div>
          <p>
            En AP, entendemos que el capital humano es el recurso más valioso. Todas nuestras
            decisiones operativas priorizan la seguridad, la salud física y mental, y el bienestar
            integral de nuestros trabajadores.
          </p>
          <p class="commitment-highlight">
            <strong>Nuestro objetivo:</strong> Que cada persona regrese a su hogar sana, segura y
            orgullosa del trabajo bien hecho.
          </p>
        </div>

        <div class="commitment-stats">
          <div v-for="(stat, index) in stats" :key="index" class="stat-box">
            <div class="stat-value">{{ stat.value }}</div>
            <div class="stat-label">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.safety {
  padding: 6rem 0;
  background: linear-gradient(180deg, #d7dce1 0%, #ffffff 100%);
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
  margin: 0 auto 2rem;
}

.section-subtitle {
  max-width: 700px;
  margin: 0 auto;
  color: var(--color-text);
  font-size: 1.1rem;
  line-height: 1.7;
}

/* SAFETY GRID */
.safety-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2.5rem;
  margin-bottom: 5rem;
}

.safety-card {
  background: var(--color-white);
  padding: 3rem 2.5rem;
  border-radius: 16px;
  text-align: center;
  transition: all 0.3s ease;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  position: relative;
  overflow: hidden;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.safety-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: var(--color-red);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.safety-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.safety-card:hover::before {
  transform: scaleX(1);
}

/* ICON */
.safety-icon-wrapper {
  width: 90px;
  height: 90px;
  background: linear-gradient(135deg, rgba(227, 30, 36, 0.1) 0%, rgba(26, 40, 66, 0.05) 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 2rem;
  transition: all 0.3s ease;
}

.safety-icon {
  width: 45px;
  height: 45px;
  color: var(--color-red);
  transition: all 0.3s ease;
}

.safety-card:hover .safety-icon-wrapper {
  background: var(--color-red);
  transform: scale(1.1);
}

.safety-card:hover .safety-icon {
  color: var(--color-white);
  transform: scale(1.15);
}

/* CONTENT */
.safety-card h3 {
  color: var(--color-navy);
  font-size: 1.4rem;
  font-weight: 800;
  margin-bottom: 1rem;
  letter-spacing: -0.5px;
}

.safety-card p {
  color: var(--color-text);
  line-height: 1.7;
  font-size: 1rem;
}

/* COMMITMENT SECTION */
.commitment-section {
  background: var(--color-navy);
  padding: 4rem 3rem;
  border-radius: 20px;
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.commitment-section::before {
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

.commitment-content {
  color: var(--color-white);
  position: relative;
  z-index: 1;
}

.commitment-header {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.header-line-red {
  width: 60px;
  height: 4px;
  background: var(--color-red);
}

.commitment-content h3 {
  font-size: 2rem;
  font-weight: 800;
  color: var(--color-white);
  letter-spacing: -0.5px;
  margin: 0;
}

.commitment-content p {
  margin-bottom: 1.5rem;
  line-height: 1.8;
  opacity: 0.95;
  font-size: 1.05rem;
}

.commitment-content p:last-child {
  margin-bottom: 0;
}

.commitment-highlight {
  padding: 1.5rem;
  background: rgba(255, 255, 255, 0.08);
  border-left: 4px solid var(--color-red);
  border-radius: 8px;
  margin-top: 2rem;
}

.commitment-highlight strong {
  color: var(--color-red);
  font-weight: 700;
}

.commitment-stats {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  position: relative;
  z-index: 1;
}

.stat-box {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(10px);
  padding: 2rem 1.5rem;
  border-radius: 12px;
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
}

.stat-box:hover {
  background: rgba(255, 255, 255, 0.12);
  border-color: var(--color-red);
  transform: translateX(-10px);
}

.stat-value {
  font-size: 3rem;
  font-weight: 900;
  color: var(--color-red);
  line-height: 1;
  margin-bottom: 0.75rem;
  text-shadow: 0 2px 10px rgba(227, 30, 36, 0.3);
}

.stat-label {
  color: var(--color-white);
  font-size: 0.95rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .safety-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }

  .commitment-section {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .commitment-stats {
    flex-direction: row;
    gap: 1.25rem;
  }
}

@media (max-width: 768px) {
  .safety {
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

  .section-subtitle {
    font-size: 1rem;
  }

  .safety-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
    margin-bottom: 3rem;
  }

  .safety-card {
    padding: 2.5rem 2rem;
  }

  .safety-icon-wrapper {
    width: 80px;
    height: 80px;
  }

  .safety-icon {
    width: 40px;
    height: 40px;
  }

  .safety-card h3 {
    font-size: 1.3rem;
  }

  .commitment-section {
    padding: 3rem 2rem;
  }

  .commitment-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
  }

  .commitment-content h3 {
    font-size: 1.6rem;
  }

  .commitment-content p {
    font-size: 1rem;
  }

  .commitment-stats {
    flex-direction: column;
  }

  .stat-box {
    padding: 1.75rem 1.25rem;
  }

  .stat-value {
    font-size: 2.5rem;
  }
}

@media (max-width: 480px) {
  .safety {
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

  .safety-card {
    padding: 2rem 1.5rem;
  }

  .safety-icon-wrapper {
    width: 70px;
    height: 70px;
  }

  .safety-icon {
    width: 35px;
    height: 35px;
  }

  .safety-card h3 {
    font-size: 1.2rem;
  }

  .safety-card p {
    font-size: 0.95rem;
  }

  .commitment-section {
    padding: 2.5rem 1.5rem;
    border-radius: 16px;
  }

  .commitment-content h3 {
    font-size: 1.4rem;
  }

  .commitment-content p {
    font-size: 0.95rem;
    margin-bottom: 1.25rem;
  }

  .commitment-highlight {
    padding: 1.25rem;
    margin-top: 1.5rem;
  }

  .stat-box {
    padding: 1.5rem 1rem;
  }

  .stat-value {
    font-size: 2.2rem;
  }

  .stat-label {
    font-size: 0.85rem;
  }
}
</style>
