<script setup lang="ts">
import ContactForm from './ContactForm.vue'
</script>

<template>
  <section id="contacto" class="contact">
    <div class="container">
      <!-- Header -->
      <div class="section-header">
        <div class="header-badge">CONTÁCTANOS</div>
        <h2 class="section-title">Contacto</h2>
        <div class="title-line"></div>
        <p class="section-subtitle">
          Estamos listos para ayudarte con tus proyectos industriales y logísticos
        </p>
      </div>

      <!-- Formulario de contacto -->
      <ContactForm />

      <!-- Información de contacto debajo -->
      <div class="contact-info-section">
        <div class="section-divider">
          <div class="divider-line"></div>
          <h3>O contáctanos directamente</h3>
          <div class="divider-line"></div>
        </div>

        <div class="contact-grid">
          <a href="mailto:victor.oyarzo@artilleriapesada.cl" class="contact-card">
            <div class="contact-icon-wrapper">
              <svg class="contact-icon" viewBox="0 0 24 24" fill="none">
                <path
                  d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <polyline
                  points="22,6 12,13 2,6"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </div>
            <div class="contact-content">
              <h4>Email</h4>
              <p>victor.oyarzo@artilleriapesada.cl</p>
            </div>
          </a>

          <a href="tel:+56942513080" class="contact-card">
            <div class="contact-icon-wrapper">
              <svg class="contact-icon" viewBox="0 0 24 24" fill="none">
                <path
                  d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </div>
            <div class="contact-content">
              <h4>Teléfono</h4>
              <p>+56 9 4251 3080</p>
            </div>
          </a>

          <div class="contact-card">
            <div class="contact-icon-wrapper">
              <svg class="contact-icon" viewBox="0 0 24 24" fill="none">
                <path
                  d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <circle
                  cx="12"
                  cy="10"
                  r="3"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </div>
            <div class="contact-content">
              <h4>Casa Matriz</h4>
              <p>1 Norte 461, Of. 703, Viña del Mar</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
  padding: 6rem 0;
  background: linear-gradient(180deg, #efdada 0%, #f8f9fa 100%);
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

/* CONTACT INFO SECTION */
.contact-info-section {
  margin-top: 5rem;
}

.section-divider {
  display: flex;
  align-items: center;
  gap: 2rem;
  margin-bottom: 4rem;
  justify-content: center;
}

.divider-line {
  flex: 1;
  max-width: 200px;
  height: 2px;
  background: linear-gradient(to right, transparent, var(--color-red), transparent);
}

.section-divider h3 {
  font-size: 2rem;
  color: var(--color-navy);
  font-weight: 800;
  letter-spacing: -0.5px;
  white-space: nowrap;
  margin: 0;
}

.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  margin-bottom: 4rem;
}

.contact-card {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  background: var(--color-white);
  padding: 2rem 1.5rem;
  border-radius: 16px;
  transition: all 0.3s ease;
  text-decoration: none;
  color: inherit;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  border: 1px solid rgba(0, 0, 0, 0.05);
  position: relative;
  overflow: hidden;
}

.contact-card::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 4px;
  background: var(--color-red);
  transform: scaleY(0);
  transition: transform 0.3s ease;
}

.contact-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
}

.contact-card:hover::before {
  transform: scaleY(1);
}

.contact-icon-wrapper {
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, rgba(227, 30, 36, 0.1) 0%, rgba(26, 40, 66, 0.05) 100%);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  transition: all 0.3s ease;
}

.contact-icon {
  width: 30px;
  height: 30px;
  color: var(--color-red);
  transition: all 0.3s ease;
}

.contact-card:hover .contact-icon-wrapper {
  background: var(--color-red);
  transform: scale(1.1);
}

.contact-card:hover .contact-icon {
  color: var(--color-white);
}

.contact-content {
  text-align: left;
  flex: 1;
}

.contact-content h4 {
  color: var(--color-navy);
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.contact-content p {
  color: var(--color-text);
  font-size: 1rem;
  font-weight: 500;
}

/* COMPANY INFO BOX */
.company-info-box {
  background: var(--color-navy);
  padding: 4rem 3rem;
  border-radius: 20px;
  color: var(--color-white);
  position: relative;
  overflow: hidden;
}

.company-info-box::before {
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

.company-header {
  text-align: center;
  margin-bottom: 3rem;
  position: relative;
  z-index: 1;
}

.company-header h3 {
  font-size: 2.2rem;
  font-weight: 800;
  margin-bottom: 0.75rem;
  letter-spacing: -0.5px;
}

.company-header p {
  font-size: 1.05rem;
  color: rgba(255, 255, 255, 0.7);
  font-weight: 500;
}

.company-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  position: relative;
  z-index: 1;
}

.company-item {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  padding: 2rem;
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(10px);
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
}

.company-item:hover {
  background: rgba(255, 255, 255, 0.12);
  border-color: var(--color-red);
  transform: translateY(-5px);
}

.company-item strong {
  color: var(--color-red);
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 1.5px;
  font-weight: 700;
}

.company-item span {
  font-size: 1.05rem;
  font-weight: 600;
  line-height: 1.5;
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .contact-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .company-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .contact {
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

  .contact-info-section {
    margin-top: 3rem;
  }

  .section-divider {
    flex-direction: column;
    gap: 1rem;
    margin-bottom: 3rem;
  }

  .divider-line {
    display: none;
  }

  .section-divider h3 {
    font-size: 1.6rem;
  }

  .contact-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
    margin-bottom: 3rem;
  }

  .contact-card {
    padding: 1.75rem 1.25rem;
  }

  .contact-icon-wrapper {
    width: 55px;
    height: 55px;
  }

  .contact-icon {
    width: 28px;
    height: 28px;
  }

  .company-info-box {
    padding: 3rem 2rem;
  }

  .company-header h3 {
    font-size: 1.8rem;
  }

  .company-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .company-item {
    padding: 1.75rem;
  }
}

@media (max-width: 480px) {
  .contact {
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

  .section-divider h3 {
    font-size: 1.4rem;
  }

  .contact-card {
    padding: 1.5rem 1rem;
    gap: 1rem;
  }

  .contact-icon-wrapper {
    width: 50px;
    height: 50px;
  }

  .contact-icon {
    width: 26px;
    height: 26px;
  }

  .contact-content h4 {
    font-size: 0.8rem;
  }

  .contact-content p {
    font-size: 0.95rem;
  }

  .company-info-box {
    padding: 2.5rem 1.5rem;
    border-radius: 16px;
  }

  .company-header h3 {
    font-size: 1.5rem;
  }

  .company-header p {
    font-size: 0.95rem;
  }

  .company-item {
    padding: 1.5rem;
  }

  .company-item strong {
    font-size: 0.75rem;
  }

  .company-item span {
    font-size: 0.95rem;
  }
}
</style>
