<script setup lang="ts">
const services = [
  {
    icon: 'logistics',
    title: 'Operaciones Portuarias y Ferroviarias',
    image: '/TORNAMESA SAI/WhatsApp Image 2025-06-05 at 17.31.53.jpeg',
    items: [
      'Transferencia, porteo y stacking de contenedores',
      'Recepción y despacho de concentrado de cobre y ánodos',
      'Carguío y descarga de trenes y camiones',
      'Gestión de patios de transferencia 24/7',
    ],
  },
  {
    icon: 'maintenance',
    title: 'Mantenimiento y Limpieza',
    image: '/LIMPIEZA PATIO LAS BLANCAS/WhatsApp Image 2025-07-08 at 12.40.05.jpeg',
    items: [
      'Mantenimiento preventivo y correctivo de equipos',
      'Limpieza profunda de patios y áreas operativas',
      'Retiro de concentrado y disposición final',
      'Habilitación de zonas críticas',
    ],
  },
  {
    icon: 'transport',
    title: 'Supervisión y Seguridad',
    image: '/CUCONS VEN/WhatsApp Image 2025-06-12 at 11.23.38.jpeg',
    items: [
      'Supervisión operativa en faena',
      'Control de seguridad y medio ambiente',
      'Gestión integral SSOMA',
      'Cumplimiento normativo y trazabilidad',
    ],
  },
  {
    icon: 'special',
    title: 'Servicios Especiales',
    image: '/DESARME Y ARMADO RS/WhatsApp Image 2025-07-31 at 10.14.17 (2).jpeg',
    items: [
      'Desarme, traslado y armado de Reach Stacker',
      'Traslados de minicargadores y grúas horquillas',
      'Asistencia operativa en faenas portuarias',
      'Servicios de emergencia 24/7',
    ],
  },
]
</script>

<template>
  <section id="servicios" class="services">
    <div class="container">
      <!-- Header -->
      <div class="section-header">
        <div class="header-badge">¿QUÉ HACEMOS?</div>
        <h2 class="section-title">Nuestros Servicios</h2>
        <div class="title-line"></div>
        <p class="section-subtitle">
          Operamos faenas portuarias y ferroviarias con enfoque en seguridad, eficiencia y
          cumplimiento normativo
        </p>
      </div>

      <!-- Services Grid -->
      <div class="services-grid">
        <div v-for="(service, index) in services" :key="index" class="service-card">
          <!-- Icon -->
          <div class="service-icon-wrapper">
            <!-- Logistics Icon -->
            <svg
              v-if="service.icon === 'logistics'"
              class="service-icon"
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

            <!-- Maintenance Icon -->
            <svg
              v-if="service.icon === 'maintenance'"
              class="service-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <circle cx="12" cy="12" r="3" stroke="currentColor" stroke-width="2" />
              <path
                d="M12 1v6m0 6v6M5.64 5.64l4.24 4.24m4.24 4.24l4.24 4.24M1 12h6m6 0h6M5.64 18.36l4.24-4.24m4.24-4.24l4.24-4.24"
                stroke="currentColor"
                stroke-width="2"
              />
            </svg>

            <!-- Transport Icon -->
            <svg
              v-if="service.icon === 'transport'"
              class="service-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <path
                d="M3 9h18M3 15h18M5 21h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v14a2 2 0 002 2z"
                stroke="currentColor"
                stroke-width="2"
              />
              <path d="M9 3v18M15 3v18" stroke="currentColor" stroke-width="2" />
            </svg>

            <!-- Special Services Icon -->
            <svg
              v-if="service.icon === 'special'"
              class="service-icon"
              viewBox="0 0 24 24"
              fill="none"
            >
              <path
                d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </div>

          <!-- Title -->
          <h3 class="service-title">{{ service.title }}</h3>

          <!-- Items List -->
          <ul class="service-list">
            <li v-for="(item, i) in service.items" :key="i">
              <svg class="check-icon" viewBox="0 0 24 24" fill="none">
                <path
                  d="M20 6L9 17l-5-5"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
              <span>{{ item }}</span>
            </li>
          </ul>

          <!-- Service Image -->
          <div class="service-image">
            <img :src="service.image" :alt="service.title" loading="lazy" />
          </div>
        </div>
      </div>

      <!-- CTA Box -->
      <div class="cta-box">
        <div class="cta-content">
          <h3>¿Quieres conocer nuestras faenas en detalle?</h3>
          <p>
            Cada operación está respaldada por procedimientos, certificaciones y un equipo
            capacitado
          </p>
          <a href="#servicios-detallados" class="cta-button">
            <span>Ver Faenas</span>
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path
                d="M4 10H16M16 10L10 4M16 10L10 16"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
              />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services {
  padding: 6rem 0;
  background: linear-gradient(180deg, #efd5d5 0%, #f8f9fa 100%);
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

/* SERVICES GRID */
.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
  gap: 2.5rem;
  margin-bottom: 4rem;
}

.service-card {
  background: var(--color-white);
  padding: 3rem 2.5rem;
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.service-card::before {
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

.service-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.service-card:hover::before {
  transform: scaleX(1);
}

/* ICON */
.service-icon-wrapper {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, rgba(227, 30, 36, 0.1) 0%, rgba(26, 40, 66, 0.05) 100%);
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 2rem;
  transition: all 0.3s ease;
}

.service-icon {
  width: 40px;
  height: 40px;
  color: var(--color-red);
  transition: all 0.3s ease;
}

.service-card:hover .service-icon-wrapper {
  background: var(--color-red);
  transform: rotate(5deg) scale(1.05);
}

.service-card:hover .service-icon {
  color: var(--color-white);
  transform: scale(1.1);
}

/* TITLE */
.service-title {
  font-size: 1.6rem;
  color: var(--color-navy);
  margin-bottom: 1.5rem;
  font-weight: 800;
  letter-spacing: -0.5px;
}

/* LIST */
.service-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.service-list li {
  padding: 0.875rem 0;
  color: var(--color-text);
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  line-height: 1.6;
  font-size: 1rem;
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
}

.service-list li:last-child {
  border-bottom: none;
}

.check-icon {
  width: 20px;
  height: 20px;
  color: var(--color-red);
  flex-shrink: 0;
  margin-top: 2px;
}

/* SERVICE IMAGE */
.service-image {
  margin-top: 1.5rem;
  border-radius: 12px;
  overflow: hidden;
  aspect-ratio: 16/9;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.service-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
}

.service-card:hover .service-image img {
  transform: scale(1.05);
}

/* CTA BOX */
.cta-box {
  background: var(--color-navy);
  padding: 4rem 3rem;
  border-radius: 20px;
  position: relative;
  overflow: hidden;
}

.cta-box::before {
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

.cta-content {
  position: relative;
  z-index: 1;
  text-align: center;
  color: var(--color-white);
}

.cta-box h3 {
  font-size: 2.2rem;
  font-weight: 800;
  margin-bottom: 1rem;
  letter-spacing: -0.5px;
}

.cta-box p {
  margin-bottom: 2.5rem;
  opacity: 0.9;
  font-size: 1.1rem;
  line-height: 1.7;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 16px 38px;
  background: var(--color-red);
  color: var(--color-white);
  text-decoration: none;
  font-weight: 600;
  font-size: 1.05rem;
  border-radius: 8px;
  transition: all 0.3s ease;
  border: 2px solid var(--color-red);
}

.cta-button:hover {
  background: var(--color-red-dark);
  border-color: var(--color-red-dark);
  transform: translateY(-3px);
  box-shadow: 0 10px 30px rgba(227, 30, 36, 0.4);
}

.cta-button svg {
  transition: transform 0.3s ease;
}

.cta-button:hover svg {
  transform: translateX(5px);
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .services-grid {
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }
}

@media (max-width: 768px) {
  .services {
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

  .services-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
    margin-bottom: 3rem;
  }

  .service-card {
    padding: 2.5rem 2rem;
  }

  .service-icon-wrapper {
    width: 70px;
    height: 70px;
  }

  .service-icon {
    width: 35px;
    height: 35px;
  }

  .service-title {
    font-size: 1.4rem;
  }

  .service-list li {
    font-size: 0.95rem;
    padding: 0.75rem 0;
  }

  .cta-box {
    padding: 3rem 2rem;
  }

  .cta-box h3 {
    font-size: 1.8rem;
  }

  .cta-box p {
    font-size: 1rem;
    margin-bottom: 2rem;
  }
}

@media (max-width: 480px) {
  .services {
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

  .section-subtitle {
    font-size: 0.95rem;
  }

  .service-card {
    padding: 2rem 1.5rem;
  }

  .service-icon-wrapper {
    width: 65px;
    height: 65px;
  }

  .service-icon {
    width: 32px;
    height: 32px;
  }

  .service-title {
    font-size: 1.3rem;
    margin-bottom: 1.25rem;
  }

  .service-list li {
    font-size: 0.9rem;
    gap: 0.75rem;
  }

  .check-icon {
    width: 18px;
    height: 18px;
  }

  .cta-box {
    padding: 2.5rem 1.5rem;
    border-radius: 16px;
  }

  .cta-box h3 {
    font-size: 1.5rem;
  }

  .cta-box p {
    font-size: 0.95rem;
  }

  .cta-button {
    padding: 14px 32px;
    font-size: 1rem;
    width: 100%;
    justify-content: center;
  }
}
</style>
