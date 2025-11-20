<script setup lang="ts">
// Component now only shows Mission & Vision
</script>

<template>
  <section id="valores" class="values">
    <div class="container">
      <!-- Header -->
      <div class="section-header">
        <div class="header-badge">NUESTRA IDENTIDAD</div>
        <h2 class="section-title">Misión y Visión</h2>
        <div class="title-line"></div>
      </div>

      <!-- Mission & Vision -->
      <div class="mission-vision">
        <div class="mv-card mission">
          <div class="mv-header">
            <div class="mv-icon">
              <svg viewBox="0 0 24 24" fill="none">
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
            <h3>Misión</h3>
          </div>
          <p>
            Brindar soluciones operativas y logísticas integrales para el manejo de maquinaria
            pesada, el carguío y la transferencia de materiales en entornos industriales, mineros y
            portuarios.
          </p>
          <p>
            Nuestra misión es asegurar la continuidad operacional de nuestros clientes mediante una
            gestión basada en la seguridad, la eficiencia y la sostenibilidad.
          </p>
        </div>

        <div class="mv-card vision">
          <div class="mv-header">
            <div class="mv-icon">
              <svg viewBox="0 0 24 24" fill="none">
                <path
                  d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <circle
                  cx="12"
                  cy="12"
                  r="3"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </div>
            <h3>Visión</h3>
          </div>
          <p>
            Ser una empresa líder y referente en operaciones de maquinaria pesada y servicios
            logísticos industriales, reconocida por su excelencia operativa, su cultura preventiva y
            su compromiso con el medio ambiente.
          </p>
          <p>
            Aspiramos a consolidar alianzas de largo plazo con nuestros clientes, transformándonos
            en un socio estratégico confiable.
          </p>
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
.values {
  padding: 6rem 0;
  background: linear-gradient(180deg, #e9eff7 0%, #ffffff 100%);
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

/* MISSION & VISION */
.mission-vision {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2.5rem;
  margin-bottom: 5rem;
}

.mv-card {
  padding: 3.5rem 3rem;
  border-radius: 20px;
  color: var(--color-white);
  position: relative;
  overflow: hidden;
}

.mv-card::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  transform: translate(30%, -30%);
}

.mission {
  background: var(--color-navy);
}

.vision {
  background: linear-gradient(135deg, var(--color-red) 0%, #c11a1f 100%);
}

.mv-header {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  margin-bottom: 2rem;
  position: relative;
  z-index: 1;
}

.mv-icon {
  width: 60px;
  height: 60px;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.mv-icon svg {
  width: 32px;
  height: 32px;
  color: var(--color-white);
}

.mv-card h3 {
  font-size: 2rem;
  font-weight: 800;
  letter-spacing: -0.5px;
  margin: 0;
}

.mv-card p {
  margin-bottom: 1.5rem;
  line-height: 1.8;
  opacity: 0.95;
  font-size: 1.05rem;
  position: relative;
  z-index: 1;
}

.mv-card p:last-child {
  margin-bottom: 0;
}

/* VALUES SECTION - Removed, now in About component */

/* QUOTE SECTION */
.quote-section {
  background: var(--color-navy);
  padding: 4rem 3rem;
  border-radius: 20px;
  text-align: center;
  position: relative;
  color: var(--color-white);
  overflow: hidden;
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
  .mission-vision {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .values-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }
}

@media (max-width: 768px) {
  .values {
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

  .mission-vision {
    margin-bottom: 3rem;
  }

  .mv-card {
    padding: 3rem 2.5rem;
  }

  .mv-header {
    gap: 1rem;
  }

  .mv-icon {
    width: 50px;
    height: 50px;
  }

  .mv-icon svg {
    width: 28px;
    height: 28px;
  }

  .mv-card h3 {
    font-size: 1.6rem;
  }

  .mv-card p {
    font-size: 1rem;
  }

  .values-section-header {
    flex-direction: column;
    gap: 1rem;
    margin-bottom: 3rem;
  }

  .header-line-red {
    display: none;
  }

  .values-title {
    font-size: 1.6rem;
  }

  .values-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
    margin-bottom: 3rem;
  }

  .value-card {
    padding: 2.5rem 2rem;
  }

  .value-icon-wrapper {
    width: 80px;
    height: 80px;
  }

  .value-icon {
    width: 40px;
    height: 40px;
  }

  .value-card h4 {
    font-size: 1.3rem;
  }

  .quote-section {
    padding: 3rem 2rem;
  }

  .quote-icon {
    width: 70px;
    height: 70px;
  }

  .quote-text {
    font-size: 1.2rem;
  }
}

@media (max-width: 480px) {
  .values {
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

  .mv-card {
    padding: 2.5rem 2rem;
    border-radius: 16px;
  }

  .mv-header {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .mv-card h3 {
    font-size: 1.4rem;
  }

  .mv-card p {
    font-size: 0.95rem;
    margin-bottom: 1.25rem;
  }

  .values-title {
    font-size: 1.4rem;
  }

  .value-card {
    padding: 2rem 1.5rem;
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
    font-size: 0.95rem;
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
}
</style>
