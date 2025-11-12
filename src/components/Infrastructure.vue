<script setup lang="ts">
const equipment = [
  {
    icon: 'loader',
    name: 'Cargadores Frontales',
    description: 'Alta capacidad para operaciones de carguío y manipulación de material a granel',
  },
  {
    icon: 'crane',
    name: 'Grúas Reach Stacker',
    description: 'Movimiento y apilamiento de contenedores y materiales de gran peso',
  },
  {
    icon: 'forklift',
    name: 'Grúas Horquillas',
    description: 'Industriales de distintas capacidades para operaciones portuarias',
  },
  {
    icon: 'truck',
    name: 'Camiones y Tractos',
    description: 'Transporte interno y porteo de carga dentro de faenas',
  },
]

const team = [
  'Jefatura de Operaciones',
  'Supervisores de Faena',
  'Operadores Certificados',
  'Conductores Profesionales',
  'Personal de Mantenimiento',
  'Asesores en Prevención de Riesgos',
  'Equipo Administrativo',
]
</script>

<template>
  <section id="infraestructura" class="infrastructure">
    <div class="container">
      <!-- Header -->
      <div class="section-header">
        <div class="header-badge">CAPACIDADES</div>
        <h2 class="section-title">Infraestructura y Recursos</h2>
        <div class="title-line"></div>
        <p class="section-subtitle">
          Infraestructura técnica y humana diseñada para garantizar operaciones seguras, eficientes
          y sostenibles
        </p>
      </div>

      <!-- Equipment Section -->
      <div class="content-section">
        <div class="subsection-header">
          <div class="header-line-red"></div>
          <h3 class="subsection-title">Equipos y Maquinaria</h3>
        </div>
        <p class="intro-text">
          Disponemos de una flota moderna y versátil de maquinaria pesada, mantenida bajo programas
          preventivos y correctivos con trazabilidad documentada.
        </p>

        <div class="equipment-grid">
          <div v-for="(item, index) in equipment" :key="index" class="equipment-card">
            <!-- Icons -->
            <div class="equipment-icon-wrapper">
              <!-- Loader Icon -->
              <svg
                v-if="item.icon === 'loader'"
                class="equipment-icon"
                viewBox="0 0 24 24"
                fill="none"
              >
                <path
                  d="M3 6h4l3 6-3 6H3M21 6h-4l-3 6 3 6h4"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <circle cx="12" cy="12" r="2" fill="currentColor" />
                <path
                  d="M8 18h8M8 6h8"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                />
              </svg>

              <!-- Crane Icon -->
              <svg
                v-if="item.icon === 'crane'"
                class="equipment-icon"
                viewBox="0 0 24 24"
                fill="none"
              >
                <path
                  d="M4 2v20M4 2h16l-4 8h-8M4 22h16"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <circle cx="16" cy="18" r="2" stroke="currentColor" stroke-width="2" />
                <path d="M16 16V10" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
              </svg>

              <!-- Forklift Icon -->
              <svg
                v-if="item.icon === 'forklift'"
                class="equipment-icon"
                viewBox="0 0 24 24"
                fill="none"
              >
                <rect x="2" y="4" width="8" height="8" stroke="currentColor" stroke-width="2" />
                <path
                  d="M10 8h6v8M10 16h6"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                />
                <circle cx="6" cy="18" r="2" stroke="currentColor" stroke-width="2" />
                <circle cx="16" cy="18" r="2" stroke="currentColor" stroke-width="2" />
                <path d="M16 4v4h6" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
              </svg>

              <!-- Truck Icon -->
              <svg
                v-if="item.icon === 'truck'"
                class="equipment-icon"
                viewBox="0 0 24 24"
                fill="none"
              >
                <rect x="1" y="3" width="15" height="13" stroke="currentColor" stroke-width="2" />
                <polygon
                  points="16 8 20 8 23 11 23 16 16 16 16 8"
                  stroke="currentColor"
                  stroke-width="2"
                />
                <circle cx="5.5" cy="18.5" r="2.5" stroke="currentColor" stroke-width="2" />
                <circle cx="18.5" cy="18.5" r="2.5" stroke="currentColor" stroke-width="2" />
              </svg>
            </div>

            <h4>{{ item.name }}</h4>
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>

      <!-- Team Section -->
      <div class="team-section">
        <div class="team-content">
          <div class="subsection-header">
            <div class="header-line-red"></div>
            <h3 class="subsection-title">Recursos Humanos y Competencias</h3>
          </div>
          <p>
            Nuestro equipo está compuesto por profesionales y técnicos con formación específica en
            seguridad, operaciones logísticas y mantenimiento de maquinaria pesada.
          </p>
          <p class="highlight-text">
            <strong>Todos nuestros trabajadores reciben capacitación periódica</strong> en
            seguridad, control ambiental, conducción defensiva y operación segura de equipos.
          </p>
        </div>

        <div class="team-list-wrapper">
          <div class="team-list-header">
            <h4>Estructura Operacional</h4>
          </div>
          <ul class="team-list">
            <li v-for="(role, index) in team" :key="index">
              <svg class="check-icon" viewBox="0 0 24 24" fill="none">
                <path
                  d="M9 12l2 2 4-4"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <circle
                  cx="12"
                  cy="12"
                  r="10"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
              <span>{{ role }}</span>
            </li>
          </ul>
        </div>
      </div>

      <!-- Commitment Box -->
      <div class="commitment-box">
        <div class="commitment-icon-wrapper">
          <svg class="commitment-icon" viewBox="0 0 24 24" fill="none">
            <path
              d="M12 2L2 7l10 5 10-5-10-5z"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M2 17l10 5 10-5M2 12l10 5 10-5"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
        <h3>Compromiso con la Seguridad y el Medio Ambiente</h3>
        <p>
          Cada faena es planificada con criterios de seguridad, eficiencia energética y control de
          impacto ambiental. Nuestros programas de trabajo contemplan medidas de mitigación de
          polvo, control de derrames, uso eficiente de recursos y cumplimiento de toda la normativa
          vigente.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.infrastructure {
  padding: 6rem 0;
  background: linear-gradient(180deg, #eee7e7 0%, #f8f9fa 100%);
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

/* CONTENT SECTION */
.content-section {
  margin-bottom: 5rem;
}

.subsection-header {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  margin-bottom: 1.5rem;
  justify-content: center;
}

.header-line-red {
  width: 60px;
  height: 4px;
  background: var(--color-red);
}

.subsection-title {
  font-size: 2rem;
  color: var(--color-navy);
  font-weight: 800;
  letter-spacing: -0.5px;
  margin: 0;
}

.intro-text {
  text-align: center;
  max-width: 800px;
  margin: 0 auto 3rem;
  color: var(--color-text);
  line-height: 1.8;
  font-size: 1.05rem;
}

/* EQUIPMENT GRID */
.equipment-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 2.5rem;
}

.equipment-card {
  background: var(--color-white);
  padding: 3rem 2rem;
  border-radius: 16px;
  text-align: center;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.equipment-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, var(--color-red) 0%, var(--color-navy) 100%);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.equipment-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.equipment-card:hover::before {
  transform: scaleX(1);
}

.equipment-icon-wrapper {
  width: 90px;
  height: 90px;
  background: linear-gradient(135deg, rgba(227, 30, 36, 0.1) 0%, rgba(26, 40, 66, 0.05) 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  transition: all 0.3s ease;
}

.equipment-icon {
  width: 45px;
  height: 45px;
  color: var(--color-red);
  transition: all 0.3s ease;
}

.equipment-card:hover .equipment-icon-wrapper {
  background: var(--color-red);
  transform: scale(1.1);
}

.equipment-card:hover .equipment-icon {
  color: var(--color-white);
  transform: scale(1.15);
}

.equipment-card h4 {
  color: var(--color-navy);
  font-size: 1.3rem;
  margin-bottom: 1rem;
  font-weight: 800;
  letter-spacing: -0.5px;
}

.equipment-card p {
  color: var(--color-text);
  line-height: 1.6;
  font-size: 1rem;
}

/* TEAM SECTION */
.team-section {
  background: var(--color-white);
  padding: 4rem 3rem;
  border-radius: 20px;
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 4rem;
  margin-bottom: 4rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}

.team-content {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.team-content .subsection-header {
  justify-content: flex-start;
}

.team-content p {
  color: var(--color-text);
  line-height: 1.8;
  font-size: 1.05rem;
}

.highlight-text {
  padding: 1.5rem;
  background: rgba(227, 30, 36, 0.05);
  border-left: 4px solid var(--color-red);
  border-radius: 8px;
}

.highlight-text strong {
  color: var(--color-navy);
  font-weight: 700;
}

.team-list-wrapper {
  background: var(--color-gray);
  padding: 2.5rem;
  border-radius: 12px;
}

.team-list-header h4 {
  color: var(--color-navy);
  margin-bottom: 2rem;
  font-size: 1.3rem;
  font-weight: 800;
  letter-spacing: -0.5px;
}

.team-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.team-list li {
  padding: 0.875rem 0;
  color: var(--color-text);
  display: flex;
  align-items: center;
  gap: 1rem;
  font-size: 1rem;
  font-weight: 500;
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
}

.team-list li:last-child {
  border-bottom: none;
}

.check-icon {
  width: 24px;
  height: 24px;
  color: var(--color-red);
  flex-shrink: 0;
}

/* COMMITMENT BOX */
.commitment-box {
  background: var(--color-navy);
  padding: 4rem 3rem;
  border-radius: 20px;
  text-align: center;
  color: var(--color-white);
  position: relative;
  overflow: hidden;
}

.commitment-box::before {
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

.commitment-icon-wrapper {
  width: 100px;
  height: 100px;
  background: rgba(227, 30, 36, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 2rem;
  position: relative;
  z-index: 1;
}

.commitment-icon {
  width: 50px;
  height: 50px;
  color: var(--color-red);
}

.commitment-box h3 {
  font-size: 2.2rem;
  font-weight: 800;
  margin-bottom: 1.5rem;
  letter-spacing: -0.5px;
  position: relative;
  z-index: 1;
}

.commitment-box p {
  max-width: 900px;
  margin: 0 auto;
  line-height: 1.8;
  opacity: 0.95;
  font-size: 1.1rem;
  position: relative;
  z-index: 1;
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .equipment-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }

  .team-section {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
}

@media (max-width: 768px) {
  .infrastructure {
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

  .content-section {
    margin-bottom: 3rem;
  }

  .subsection-header {
    flex-direction: column;
    gap: 1rem;
  }

  .subsection-title {
    font-size: 1.6rem;
  }

  .intro-text {
    font-size: 1rem;
    margin-bottom: 2rem;
  }

  .equipment-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .equipment-card {
    padding: 2.5rem 2rem;
  }

  .equipment-icon-wrapper {
    width: 80px;
    height: 80px;
  }

  .equipment-icon {
    width: 40px;
    height: 40px;
  }

  .equipment-card h4 {
    font-size: 1.2rem;
  }

  .team-section {
    padding: 3rem 2rem;
    margin-bottom: 3rem;
  }

  .team-content p {
    font-size: 1rem;
  }

  .team-list-wrapper {
    padding: 2rem;
  }

  .team-list-header h4 {
    font-size: 1.2rem;
    margin-bottom: 1.5rem;
  }

  .team-list li {
    font-size: 0.95rem;
  }

  .commitment-box {
    padding: 3rem 2rem;
  }

  .commitment-icon-wrapper {
    width: 90px;
    height: 90px;
  }

  .commitment-icon {
    width: 45px;
    height: 45px;
  }

  .commitment-box h3 {
    font-size: 1.8rem;
  }

  .commitment-box p {
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .infrastructure {
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

  .equipment-card {
    padding: 2rem 1.5rem;
  }

  .equipment-icon-wrapper {
    width: 70px;
    height: 70px;
  }

  .equipment-icon {
    width: 35px;
    height: 35px;
  }

  .equipment-card h4 {
    font-size: 1.15rem;
  }

  .equipment-card p {
    font-size: 0.95rem;
  }

  .team-section {
    padding: 2.5rem 1.5rem;
  }

  .team-list-wrapper {
    padding: 1.75rem;
  }

  .team-list li {
    font-size: 0.9rem;
    padding: 0.75rem 0;
  }

  .check-icon {
    width: 20px;
    height: 20px;
  }

  .commitment-box {
    padding: 2.5rem 1.5rem;
    border-radius: 16px;
  }

  .commitment-icon-wrapper {
    width: 80px;
    height: 80px;
  }

  .commitment-icon {
    width: 40px;
    height: 40px;
  }

  .commitment-box h3 {
    font-size: 1.5rem;
  }

  .commitment-box p {
    font-size: 0.95rem;
  }
}
</style>
