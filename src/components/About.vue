<script setup lang="ts">
import { ref } from 'vue'

const stats = [
  { number: '2022', label: 'Año de Fundación' },
  { number: '10+', label: 'Años de Experiencia del Equipo' },
  { number: '99%', label: 'Continuidad Operacional' },
  { number: '0', label: 'Accidentes con Tiempo Perdido' },
]

const identity = [
  {
    title: 'Razón Social',
    value: 'Artillería Pesada Reparación Industrial SpA',
  },
  {
    title: 'RUT',
    value: '77.540.751-4',
  },
  {
    title: 'Representante Legal',
    value: 'Angelo Cisternas Muñoz',
  },
  {
    title: 'Casa Matriz',
    value: '1 Norte 461, Oficina 703, Viña del Mar',
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
            <h3>Historia Corporativa</h3>
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

      <!-- Identity Section -->
      <div class="identity-section">
        <div class="identity-header">
          <h3>Identidad Empresarial</h3>
          <p>Información legal y contacto corporativo</p>
        </div>
        <div class="identity-grid">
          <div v-for="(item, index) in identity" :key="index" class="identity-card">
            <div class="identity-title">{{ item.title }}</div>
            <div class="identity-value">{{ item.value }}</div>
          </div>
        </div>
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

/* RESPONSIVE */
@media (max-width: 1024px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .stats-grid {
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
