<script setup lang="ts">
const currentYear = new Date().getFullYear()

const navigation = [
  { name: 'Inicio', href: '#inicio' },
  { name: 'Nosotros', href: '#nosotros' },
  { name: 'Servicios', href: '#servicios' },
  { name: 'Nuestras Faenas', href: '#servicios-detallados' },
  { name: 'Contacto', href: '#contacto' },
]

const contact = [
  {
    icon: 'email',
    text: 'victor.oyarzo@artilleriapesada.cl',
    href: 'mailto:victor.oyarzo@artilleriapesada.cl',
  },
  {
    icon: 'phone',
    text: '+56 9 4251 3080',
    href: 'tel:+56942513080',
  },
]
</script>

<template>
  <footer class="footer">
    <div class="container">
      <!-- Main Content -->
      <div class="footer-content">
        <!-- Brand Section -->
        <div class="footer-brand">
          <div class="logo-section">
            <img src="/logo.png" alt="Artillería Pesada" class="footer-logo" />
            <div class="logo-text">
              <span class="brand-name">ARTILLERÍA PESADA</span>
              <span class="brand-subtitle">Reparación Industrial SpA</span>
            </div>
          </div>
          <p class="tagline">
            En AP trabajamos cada día para mover lo que el mundo necesita, con seguridad, precisión
            y excelencia.
          </p>
        </div>

        <!-- Navigation Links -->
        <div class="footer-section">
          <h4 class="section-title">Navegación</h4>
          <ul class="footer-links">
            <li v-for="item in navigation" :key="item.name">
              <a :href="item.href">
                <svg class="link-icon" viewBox="0 0 24 24" fill="none">
                  <path
                    d="M9 18l6-6-6-6"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />
                </svg>
                {{ item.name }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Contact Info -->
        <div class="footer-section">
          <h4 class="section-title">Contacto</h4>
          <ul class="contact-list">
            <li v-for="item in contact" :key="item.text">
              <a :href="item.href" class="contact-link">
                <!-- Email Icon -->
                <svg
                  v-if="item.icon === 'email'"
                  class="contact-icon"
                  viewBox="0 0 24 24"
                  fill="none"
                >
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

                <!-- Phone Icon -->
                <svg
                  v-if="item.icon === 'phone'"
                  class="contact-icon"
                  viewBox="0 0 24 24"
                  fill="none"
                >
                  <path
                    d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />
                </svg>

                <!-- Web Icon -->
                <svg
                  v-if="item.icon === 'web'"
                  class="contact-icon"
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
                  <line
                    x1="2"
                    y1="12"
                    x2="22"
                    y2="12"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />
                  <path
                    d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />
                </svg>

                <span>{{ item.text }}</span>
              </a>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="footer-bottom">
        <div class="copyright">
          <svg class="copyright-icon" viewBox="0 0 24 24" fill="none">
            <circle
              cx="12"
              cy="12"
              r="10"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M14.5 9.5c-.9-.9-2.2-1.5-3.5-1.5-2.8 0-5 2.2-5 5s2.2 5 5 5c1.3 0 2.6-.6 3.5-1.5"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
          <span>{{ currentYear }} Artillería Pesada Reparación Industrial SpA.</span>
        </div>
        <div class="legal">Todos los derechos reservados</div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--color-navy);
  color: var(--color-white);
  padding: 4rem 0 0;
  position: relative;
  overflow: hidden;
}

.footer::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(227, 30, 36, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  transform: translate(30%, -30%);
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
  position: relative;
  z-index: 1;
}

/* FOOTER CONTENT */
.footer-content {
  display: grid;
  grid-template-columns: 2fr 1fr 1.5fr;
  gap: 4rem;
  margin-bottom: 4rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

/* BRAND SECTION */
.footer-brand {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.logo-section {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.footer-logo {
  width: 70px;
  height: 70px;
  object-fit: contain;
  filter: drop-shadow(0 0 15px rgba(227, 30, 36, 0.3));
}

.logo-text {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.brand-name {
  font-size: 1.5rem;
  font-weight: 900;
  color: var(--color-white);
  letter-spacing: -0.5px;
  line-height: 1;
}

.brand-subtitle {
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.7);
  font-weight: 600;
}

.tagline {
  font-size: 1.05rem;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.8);
  font-style: italic;
  padding-left: 1rem;
  border-left: 3px solid var(--color-red);
}

.company-info {
  display: flex;
  gap: 0.75rem;
  align-items: center;
  padding: 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 8px;
  font-size: 0.95rem;
}

.info-label {
  color: var(--color-red);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 0.85rem;
}

/* FOOTER SECTIONS */
.footer-section {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.section-title {
  color: var(--color-white);
  font-size: 1.2rem;
  font-weight: 800;
  letter-spacing: -0.5px;
  position: relative;
  padding-bottom: 0.75rem;
}

.section-title::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  width: 40px;
  height: 3px;
  background: var(--color-red);
}

/* NAVIGATION LINKS */
.footer-links {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.footer-links li a {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 500;
  transition: all 0.3s ease;
  padding: 0.5rem 0;
}

.link-icon {
  width: 16px;
  height: 16px;
  color: var(--color-red);
  transition: transform 0.3s ease;
}

.footer-links li a:hover {
  color: var(--color-white);
  padding-left: 0.5rem;
}

.footer-links li a:hover .link-icon {
  transform: translateX(3px);
}

/* CONTACT LIST */
.contact-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.contact-link {
  display: flex;
  align-items: center;
  gap: 0.875rem;
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-size: 0.95rem;
  transition: all 0.3s ease;
  padding: 0.75rem;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.03);
}

.contact-icon {
  width: 20px;
  height: 20px;
  color: var(--color-red);
  flex-shrink: 0;
  transition: all 0.3s ease;
}

.contact-link:hover {
  color: var(--color-white);
  background: rgba(255, 255, 255, 0.08);
  padding-left: 1rem;
}

.contact-link:hover .contact-icon {
  transform: scale(1.15);
}

/* FOOTER BOTTOM */
.footer-bottom {
  padding: 2rem 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.9rem;
}

.copyright {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 500;
}

.copyright-icon {
  width: 18px;
  height: 18px;
  color: var(--color-red);
}

.legal {
  font-weight: 600;
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .footer-content {
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
  }

  .footer-brand {
    grid-column: 1 / -1;
  }
}

@media (max-width: 768px) {
  .footer {
    padding: 3rem 0 0;
  }

  .container {
    padding: 0 1.5rem;
  }

  .footer-content {
    grid-template-columns: 1fr;
    gap: 2.5rem;
    margin-bottom: 2.5rem;
    padding-bottom: 2rem;
  }

  .footer-brand {
    grid-column: 1;
  }

  .logo-section {
    gap: 1rem;
  }

  .footer-logo {
    width: 60px;
    height: 60px;
  }

  .brand-name {
    font-size: 1.3rem;
  }

  .brand-subtitle {
    font-size: 0.85rem;
  }

  .tagline {
    font-size: 1rem;
  }

  .footer-bottom {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
    padding: 1.5rem 0;
  }

  .copyright {
    flex-direction: column;
    gap: 0.5rem;
  }
}

@media (max-width: 480px) {
  .footer {
    padding: 2.5rem 0 0;
  }

  .container {
    padding: 0 1rem;
  }

  .footer-content {
    gap: 2rem;
    margin-bottom: 2rem;
  }

  .logo-section {
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
  }

  .footer-logo {
    width: 55px;
    height: 55px;
  }

  .brand-name {
    font-size: 1.2rem;
  }

  .brand-subtitle {
    font-size: 0.8rem;
  }

  .tagline {
    font-size: 0.95rem;
    padding-left: 0.75rem;
  }

  .company-info {
    padding: 0.875rem;
    font-size: 0.9rem;
  }

  .info-label {
    font-size: 0.8rem;
  }

  .section-title {
    font-size: 1.1rem;
  }

  .footer-links li a,
  .contact-link {
    font-size: 0.9rem;
  }

  .contact-link {
    padding: 0.625rem;
  }

  .footer-bottom {
    font-size: 0.85rem;
  }

  .copyright span {
    text-align: center;
    line-height: 1.4;
  }
}
</style>
