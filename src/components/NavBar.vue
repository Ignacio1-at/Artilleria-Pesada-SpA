<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps<{
  activeSection: string
}>()

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const menuItems = [
  { id: 'inicio', label: 'Inicio' },
  { id: 'nosotros', label: 'Nosotros' },
  { id: 'servicios', label: 'Servicios' },
  { id: 'seguridad', label: 'Seguridad' },
  { id: 'infraestructura', label: 'Infraestructura' },
  { id: 'valores', label: 'Valores' },
  { id: 'contacto', label: 'Contacto' },
]
</script>

<template>
  <nav :class="['navbar', { scrolled: isScrolled }]">
    <div class="container">
      <a href="#inicio" class="logo" @click="closeMobileMenu">
        <div class="logo-image-wrapper">
          <img src="/logo.png" alt="Artillería Pesada" class="logo-image" />
        </div>
        <div class="logo-text-wrapper">
          <span class="logo-title">ARTILLERÍA PESADA</span>
          <span class="logo-subtitle">Reparación Industrial SpA</span>
        </div>
      </a>

      <!-- Hamburger Menu Button -->
      <button
        class="mobile-menu-btn"
        :class="{ active: isMobileMenuOpen }"
        @click="toggleMobileMenu"
        aria-label="Toggle menu"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <!-- Navigation Menu -->
      <ul :class="['nav-menu', { 'mobile-open': isMobileMenuOpen }]">
        <li v-for="item in menuItems" :key="item.id">
          <a
            :href="`#${item.id}`"
            :class="{ active: props.activeSection === item.id }"
            @click="closeMobileMenu"
          >
            {{ item.label }}
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: var(--color-white);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.08);
  z-index: 1000;
  transition: all var(--transition-normal);
}

.navbar.scrolled {
  background: var(--color-navy);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.2);
}

.navbar.scrolled .logo-title,
.navbar.scrolled .logo-subtitle {
  color: var(--color-white);
}

.navbar.scrolled .logo-image-wrapper {
  background: var(--color-white);
  box-shadow: 0 0 15px rgba(227, 30, 36, 0.3);
}

.navbar.scrolled .nav-menu a {
  color: var(--color-white);
}

.navbar.scrolled .mobile-menu-btn span {
  background: var(--color-white);
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: var(--navbar-height);
  position: relative;
}

.logo {
  display: flex;
  align-items: center;
  gap: var(--spacing-md);
  text-decoration: none;
  z-index: 1001;
  transition: transform var(--transition-normal);
}

.logo:hover {
  transform: scale(1.02);
}

.logo-image-wrapper {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: var(--color-gray-light);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 5px;
  transition: all var(--transition-normal);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.logo-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.logo-text-wrapper {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.logo-title {
  font-size: 1.1rem;
  font-weight: 800;
  color: var(--color-navy);
  letter-spacing: 0.5px;
  line-height: 1;
  transition: color var(--transition-normal);
}

.logo-subtitle {
  font-size: 0.7rem;
  color: var(--color-red);
  font-weight: 600;
  letter-spacing: 0.3px;
  line-height: 1;
  transition: color var(--transition-normal);
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
  z-index: 1001;
  border-radius: var(--border-radius-sm);
  transition: background var(--transition-normal);
}

.mobile-menu-btn:hover {
  background: rgba(227, 30, 36, 0.1);
}

.mobile-menu-btn span {
  width: 25px;
  height: 3px;
  background: var(--color-navy);
  transition: all var(--transition-normal);
  border-radius: 2px;
}

.mobile-menu-btn.active span:nth-child(1) {
  transform: rotate(45deg) translate(8px, 8px);
}

.mobile-menu-btn.active span:nth-child(2) {
  opacity: 0;
}

.mobile-menu-btn.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -7px);
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: var(--spacing-xl);
  margin: 0;
  padding: 0;
}

.nav-menu a {
  text-decoration: none;
  color: var(--color-navy);
  font-weight: 600;
  font-size: 0.95rem;
  transition: all var(--transition-normal);
  position: relative;
  padding: 0.5rem 0;
  letter-spacing: 0.3px;
}

.nav-menu a::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  width: 0;
  height: 2px;
  background: var(--color-red);
  transition: all var(--transition-normal);
  transform: translateX(-50%);
}

.nav-menu a:hover::before,
.nav-menu a.active::before {
  width: 100%;
}

.nav-menu a:hover,
.nav-menu a.active {
  color: var(--color-red);
}

/* RESPONSIVE */
@media (max-width: 1024px) {
  .nav-menu {
    gap: var(--spacing-md);
  }

  .nav-menu a {
    font-size: var(--font-size-sm);
  }
}

@media (max-width: 768px) {
  .mobile-menu-btn {
    display: flex;
  }

  .logo-image-wrapper {
    width: 45px;
    height: 45px;
  }

  .logo-title {
    font-size: 0.95rem;
  }

  .logo-subtitle {
    font-size: 0.65rem;
  }

  .nav-menu {
    position: fixed;
    top: var(--navbar-height);
    left: 0;
    right: 0;
    flex-direction: column;
    background: var(--color-navy);
    padding: var(--spacing-lg);
    gap: 0;
    transform: translateX(100%);
    transition: transform var(--transition-normal);
    box-shadow: var(--shadow-lg);
    max-height: calc(100vh - var(--navbar-height));
    overflow-y: auto;
  }

  .nav-menu.mobile-open {
    transform: translateX(0);
  }

  .nav-menu li {
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  .nav-menu li:last-child {
    border-bottom: none;
  }

  .nav-menu a {
    color: var(--color-white);
    display: block;
    padding: var(--spacing-md);
    font-size: var(--font-size-lg);
  }

  .nav-menu a::before {
    display: none;
  }

  .nav-menu a.active {
    background: rgba(227, 30, 36, 0.15);
    border-left: 4px solid var(--color-red);
    padding-left: calc(var(--spacing-md) - 4px);
  }
}

@media (max-width: 480px) {
  .logo-text-wrapper {
    display: none;
  }

  .logo-image-wrapper {
    width: 45px;
    height: 45px;
  }
}
</style>
