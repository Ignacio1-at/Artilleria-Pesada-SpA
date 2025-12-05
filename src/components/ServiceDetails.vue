<template>
  <section id="servicios-detallados" class="service-details">
    <div class="container">
      <!-- Header -->
      <div class="section-header">
        <div class="header-badge">EXPERIENCIA OPERATIVA</div>
        <h2 class="section-title">Nuestras Faenas</h2>
        <div class="title-line"></div>
        <p class="section-subtitle">
          Operaciones activas que demuestran nuestra capacidad técnica y compromiso con la
          excelencia
        </p>
      </div>

      <!-- Tabs -->
      <div class="tabs-container">
        <button
          v-for="(faena, index) in faenas"
          :key="index"
          :class="['tab-button', { active: activeFaena === index }]"
          @click="selectFaena(index)"
        >
          {{ faena.tabName || faena.title }}
        </button>
      </div>

      <!-- Contenido -->
      <div class="faena-content" v-if="currentFaena">
        <div class="faena-header">
          <div class="status-badge" :class="currentFaena.status" v-if="currentFaena.status">
            <div class="status-dot"></div>
            <span>{{ currentFaena.status === 'active' ? 'En Ejecución' : 'Finalizada' }}</span>
          </div>
          <h3 class="faena-title">{{ currentFaena.title }}</h3>
          <div class="location">
            <svg viewBox="0 0 24 24" fill="none">
              <path
                d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"
                stroke="currentColor"
                stroke-width="2"
              />
              <circle cx="12" cy="10" r="3" stroke="currentColor" stroke-width="2" />
            </svg>
            {{ currentFaena.location }}
          </div>
        </div>

        <div class="faena-info">
          <div class="info-grid">
            <div class="info-item" v-if="currentFaena.cliente">
              <svg viewBox="0 0 24 24" fill="none">
                <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2" stroke="currentColor" />
                <circle cx="9" cy="7" r="4" stroke="currentColor" />
              </svg>
              <div>
                <span class="label">Cliente</span>
                <span class="value">{{ currentFaena.cliente }}</span>
              </div>
            </div>

            <div class="info-item" v-if="currentFaena.mandante">
              <svg viewBox="0 0 24 24" fill="none">
                <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2" stroke="currentColor" />
                <circle cx="9" cy="7" r="4" stroke="currentColor" />
              </svg>
              <div>
                <span class="label">Mandante</span>
                <span class="value">{{ currentFaena.mandante }}</span>
              </div>
            </div>

            <div class="info-item" v-if="currentFaena.duracion">
              <svg viewBox="0 0 24 24" fill="none">
                <rect x="3" y="4" width="18" height="18" rx="2" stroke="currentColor" />
                <line x1="16" y1="2" x2="16" y2="6" stroke="currentColor" />
                <line x1="8" y1="2" x2="8" y2="6" stroke="currentColor" />
                <line x1="3" y1="10" x2="21" y2="10" stroke="currentColor" />
              </svg>
              <div>
                <span class="label">Duración</span>
                <span class="value">{{ currentFaena.duracion }}</span>
              </div>
            </div>

            <div class="info-item" v-if="currentFaena.turno">
              <svg viewBox="0 0 24 24" fill="none">
                <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2" stroke="currentColor" />
                <circle cx="12" cy="7" r="4" stroke="currentColor" />
              </svg>
              <div>
                <span class="label">Turno</span>
                <span class="value">{{ currentFaena.turno }}</span>
              </div>
            </div>

            <div class="info-item" v-if="currentFaena.periodicidad">
              <svg viewBox="0 0 24 24" fill="none">
                <circle cx="12" cy="12" r="10" stroke="currentColor" />
                <polyline points="12 6 12 12 16 14" stroke="currentColor" />
              </svg>
              <div>
                <span class="label">Periodicidad</span>
                <span class="value">{{ currentFaena.periodicidad }}</span>
              </div>
            </div>
          </div>

          <div class="description">
            <h4>Descripción General</h4>
            <p>{{ currentFaena.descripcion }}</p>
          </div>

          <div v-if="currentFaena.indicadores?.length" class="indicadores">
            <h4>Indicadores Operacionales</h4>
            <ul>
              <li v-for="(item, idx) in currentFaena.indicadores" :key="idx">
                <svg viewBox="0 0 24 24" fill="none">
                  <path d="M20 6L9 17l-5-5" stroke="currentColor" stroke-width="2" />
                </svg>
                {{ item }}
              </li>
            </ul>
          </div>

          <div v-if="currentFaena.dotacion?.length" class="dotacion">
            <h4>Dotación</h4>
            <ul>
              <li v-for="(item, idx) in currentFaena.dotacion" :key="idx">
                <svg viewBox="0 0 24 24" fill="none">
                  <path d="M20 6L9 17l-5-5" stroke="currentColor" stroke-width="2" />
                </svg>
                {{ item }}
              </li>
            </ul>
          </div>

          <div v-if="currentFaena.equipamiento?.length" class="equipamiento">
            <h4>Equipamiento</h4>
            <ul>
              <li v-for="(item, idx) in currentFaena.equipamiento" :key="idx">
                <svg viewBox="0 0 24 24" fill="none">
                  <path d="M20 6L9 17l-5-5" stroke="currentColor" stroke-width="2" />
                </svg>
                {{ item }}
              </li>
            </ul>
          </div>

          <div v-if="currentFaena.alcance?.length" class="alcance">
            <h4>Alcance del Servicio</h4>
            <ul>
              <li v-for="(item, idx) in currentFaena.alcance" :key="idx">
                <svg viewBox="0 0 24 24" fill="none">
                  <path d="M20 6L9 17l-5-5" stroke="currentColor" stroke-width="2" />
                </svg>
                {{ item }}
              </li>
            </ul>
          </div>

          <div v-if="currentFaena.fortalezas?.length" class="fortalezas">
            <h4>Fortalezas</h4>
            <ul>
              <li v-for="(item, idx) in currentFaena.fortalezas" :key="idx">
                <svg viewBox="0 0 24 24" fill="none">
                  <path d="M20 6L9 17l-5-5" stroke="currentColor" stroke-width="2" />
                </svg>
                {{ item }}
              </li>
            </ul>
          </div>

          <div v-if="currentFaena.servicios?.length" class="servicios">
            <h4>Servicios Realizados</h4>
            <ul>
              <li v-for="(item, idx) in currentFaena.servicios" :key="idx">
                <svg viewBox="0 0 24 24" fill="none">
                  <path d="M20 6L9 17l-5-5" stroke="currentColor" stroke-width="2" />
                </svg>
                {{ item }}
              </li>
            </ul>
          </div>
        </div>

        <!-- Galería -->
        <div class="gallery">
          <h4>Galería de Imágenes</h4>
          <div class="gallery-grid">
            <div
              v-for="(foto, idx) in currentFaena.fotos"
              :key="idx"
              class="gallery-item"
              @click="openModal(idx)"
            >
              <img :src="foto" :alt="`Foto ${idx + 1}`" loading="lazy" />
              <div class="overlay">
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
      </div>

      <!-- Modal -->
      <Transition name="modal">
        <div v-if="modalOpen && currentFaena" class="modal" @click="closeModal">
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

            <img
              :src="currentFaena.fotos[currentImageIndex]"
              :alt="`Imagen ${currentImageIndex + 1}`"
            />

            <button class="modal-nav next" @click="nextImage">
              <svg viewBox="0 0 24 24" fill="none">
                <polyline points="9 18 15 12 9 6" stroke="currentColor" stroke-width="3" />
              </svg>
            </button>

            <div class="modal-counter">
              {{ currentImageIndex + 1 }} / {{ currentFaena.fotos.length }}
            </div>
          </div>
        </div>
      </Transition>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

interface Faena {
  title: string
  tabName?: string
  location: string
  duracion?: string
  turno?: string
  status?: 'active' | 'completed'
  descripcion: string
  alcance?: string[]
  cliente?: string
  mandante?: string
  periodicidad?: string
  servicios?: string[]
  indicadores?: string[]
  dotacion?: string[]
  equipamiento?: string[]
  fortalezas?: string[]
  fotos: string[]
}

const activeFaena = ref(0)
const modalOpen = ref(false)
const currentImageIndex = ref(0)

const faenas: Faena[] = [
  {
    title:
      'Servicio de Transferencia / porteo de contenedores y/o tolvas con concentrado de cobre en Ventanas',
    tabName: 'Cucons VEN',
    location: 'Ventanas, Puchuncaví',
    duracion: 'Enero 2023 – Diciembre 2026',
    turno: '6x1',
    status: 'active',
    cliente: 'Ferrocarriles del Pacífico S.A.',
    mandante: 'Codelco División Teniente',
    descripcion:
      'En el patio de transferencia Cucons, operamos el proceso completo de movimiento de contenedores con concentrado de cobre, coordinando ingreso de camiones, corte de sellos, descarga en galpón, porteo y despacho final. La operación exige estándares estrictos por exposición a sílice y control ambiental.',
    indicadores: [
      '2023: 6.199 toneladas porteadas — 7.559 contenedores movidos',
      '2024: 1.446 toneladas — 7.814 contenedores movidos',
      '2025: 4.380 toneladas — 3.907 contenedores a la fecha',
      '100% cumplimiento sin reclamos del cliente',
      '0 accidentabilidad',
      'Tiempo promedio de ciclo: 5 minutos por contenedor',
      '~6.500 HH anuales',
    ],
    dotacion: ['1 Supervisor', '2 Operadores Reach Stacker', '2 Conductores'],
    equipamiento: ['Reach Stacker Hyster RS45-31CH', '3 camiones propios (para porteo interno)'],
    alcance: [
      'Recepción de contenedores',
      'Trazabilidad y control de sellos',
      'Descarga con protección respiratoria obligatoria por sílice',
      'Transporte interno en zona autorizada',
      'Estacionamiento, destare y retorno',
      'Aplicación rigurosa de PT-SST-03',
    ],
    fortalezas: [
      'Operación certificada y auditada permanentemente por cliente y ACHS',
      'Protocolos reforzados contra exposición a sílice',
      'Cero desviaciones en estándares ambientales y operacionales',
    ],
    fotos: [
      '/CUCONS VEN/CUCONS-VEN1.jpg',
      '/CUCONS VEN/CUCONS-VEN2.jpg',
      '/CUCONS VEN/CUCONS-VEN3.jpg',
    ],
  },
  {
    title: 'Faena Tornamesa – Barrancas, San Antonio',
    tabName: 'Tornamesa SAI',
    location: 'Barrancas, San Antonio',
    duracion: 'Enero 2024 – Diciembre 2028',
    turno: '6x1',
    status: 'active',
    cliente: 'Ferrocarriles del Pacífico S.A.',
    mandante: 'NN',
    descripcion:
      'En esta faena operamos el patio de transferencia ferroviaria ubicado en el sector Tornamesa de FEPASA, desempeñando el carguío, descarga, porteo interno y apilamiento de contenedores provenientes de trenes de carga que abastecen el puerto de San Antonio. La operación exige continuidad total y altos niveles de coordinación con las maniobras del ferrocarril. Movilizamos contenedores de carga general —desde celulosa hasta carga refrigerada o seca— garantizando trazabilidad, orden y continuidad operacional en todo momento.',
    indicadores: [
      '18.000 contenedores movilizados por año',
      '7.000 toneladas mensuales promedio',
      '17.100 HH sin accidentes (con y sin tiempo perdido)',
      '100% de cumplimiento operacional',
      'Cero quiebres de servicio desde el inicio de la faena',
    ],
    dotacion: ['1 Supervisor', '2 Operadores Reach Stacker', '2 Auxiliares de Patio'],
    equipamiento: ['Reach Stacker Hyster RS45-31CH (45 toneladas)'],
    alcance: [
      'Descarga de contenedores desde tren',
      'Porteo interno hacia patio operacional',
      'Apilamiento escalonado hasta 4 alturas según condición del terreno',
      'Control de trazabilidad digital de ingreso, stacking y despacho',
      'Coordinación con FEPASA y Puerto San Antonio',
      'Cumplimiento estricto de procedimientos internos AP (PT-SST-06)',
    ],
    fortalezas: [
      'Continuidad operacional impecable incluso ante fallas mecánicas o aumentos de demanda',
      'Sistema de vigilancia 24/7 (Tepille)',
      'Reacción inmediata ante emergencias, clima adverso o alta congestión operativa',
    ],
    fotos: [
      '/TORNAMESA SAI/TORNAMESA-1.jpg',
      '/TORNAMESA SAI/TORNAMESA-2.jpg',
      '/TORNAMESA SAI/TORNAMESA-3.jpg',
    ],
  },
  {
    title: 'Faena EFE Norte – San Antonio',
    tabName: 'EFE Norte SAI',
    location: 'San Antonio',
    duracion: 'Enero 2024 – Diciembre 2028',
    turno: '6x1',
    status: 'active',
    cliente: 'Ferrocarriles del Pacífico S.A.',
    mandante: 'Anglo American',
    descripcion:
      'Servicio de recepción, descarga, almacenamiento y despacho de ánodos de cobre. Faena especializada en la transferencia de ánodos de cobre desde trenes y su despacho posterior a camiones. Esta operación requiere precisión absoluta debido al peso y características de la carga, así como coordinación continua entre operadores, auxiliares de patio y supervisor. Contamos con procedimientos desarrollados exclusivamente para esta faena, con énfasis en el tránsito, delimitación estricta del área de maniobra y control de riesgo de atrapamiento o aplastamiento.',
    alcance: [
      'Descarga de paquetes de ánodos desde carros ferroviarios',
      'Nivelación y ajuste de paquetes mediante tocones',
      'Traslado interno seguro con grúas horquilla',
      'Preparación y carga de camiones',
      'Control documental y trazabilidad',
      'Delimitación estricta de área crítica (uso obligatorio de conos y señalización)',
    ],
    dotacion: ['1 Supervisor', '2 Operadores de Grúa Horquilla', '2 Auxiliares de Patio'],
    equipamiento: ['Grúas horquillas de alto tonelaje (según procedimiento FR-PPA-12)'],
    indicadores: [
      '0 accidentabilidad',
      'Cumplimiento estricto de distancias de seguridad (8 metros hombre–máquina)',
      'Operación validada bajo PT-SST-07, versión 03 (2025)',
    ],
    fortalezas: [
      'Alta especialización en manipulación de materiales pesados',
      'Control exhaustivo de accesos y tránsito en área de maniobra',
      'Procedimientos validados por inspecciones del cliente y ACHS',
    ],
    fotos: ['/EFE NORTE SAI/EFE-1.jpg', '/EFE NORTE SAI/EFE-2.jpg', '/EFE NORTE SAI/EFE-3.jpg'],
  },
  {
    title: 'Faena Puerto Panul – San Antonio',
    tabName: 'Puerto Panul SAI',
    location: 'Puerto Panul, San Antonio',
    duracion: 'Octubre 2023 – Enero 2025',
    turno: '6x1',
    status: 'completed',
    cliente: 'Ferrocarriles del Pacífico S.A.',
    mandante: 'NN',
    descripcion:
      'Esta faena implica el movimiento de carros ferroviarios con un minicargador para operaciones de transferencia de granel sólido en Puerto Panul. El trabajo es intermitente pero crítico, ya que debe ejecutarse con rapidez y seguridad para no interrumpir el proceso portuario.',
    alcance: [
      'Movimiento y posicionamiento de carros',
      'Apoyo a operaciones de descarga de granel',
      'Aseo y ordenamiento operacional',
    ],
    fortalezas: [
      'Respuesta rápida ante ventanas operativas del puerto',
      'Personal altamente experimentado para maniobras en zonas portuarias',
    ],
    fotos: [
      '/PUERTO PANUL SAI/WhatsApp Image 2025-07-31 at 10.06.28.jpeg',
      '/PUERTO PANUL SAI/WhatsApp Image 2025-07-31 at 10.13.02.jpeg',
    ],
  },
  {
    title: 'Faena Las Blancas – Llay Llay',
    tabName: 'Limpieza Patio Las Blancas',
    location: 'Llay Llay',
    duracion: 'Servicio Spot',
    periodicidad: 'Servicios programados según requerimiento del cliente "Servicio Spot"',
    status: 'completed',
    descripcion:
      'Realizamos limpieza integral del patio donde se acopia y transfiere concentrado de cobre, incluyendo remoción de material adherido, despeje de áreas operativas, demarcaciones, mantenimiento de señalética y disposición final autorizada.',
    alcance: [
      'Limpieza mecánica y manual',
      'Retiro de concentrado',
      'Pintura y ordenamiento de señaléticas',
      'Control de polvo y residuos',
      'Disposición final ambientalmente responsable',
    ],
    fortalezas: [
      'Conocimiento profundo de estándares ambientales del rubro',
      'Operación rápida para habilitación de zonas críticas',
    ],
    fotos: [
      '/LIMPIEZA PATIO LAS BLANCAS/WhatsApp Image 2025-07-08 at 12.39.49.jpeg',
      '/LIMPIEZA PATIO LAS BLANCAS/WhatsApp Image 2025-07-08 at 12.39.43.jpeg',
      '/LIMPIEZA PATIO LAS BLANCAS/WhatsApp Image 2025-07-08 at 12.38.09 (1).jpeg',
      '/LIMPIEZA PATIO LAS BLANCAS/WhatsApp Image 2025-07-08 at 12.39.42.jpeg',
      '/LIMPIEZA PATIO LAS BLANCAS/WhatsApp Image 2025-07-08 at 12.40.28.jpeg',
      '/LIMPIEZA PATIO LAS BLANCAS/WhatsApp Image 2025-07-08 at 12.40.35 (1).jpeg',
    ],
  },
]

// Computed property para la faena actual
const currentFaena = computed(() => faenas[activeFaena.value])

const selectFaena = (index: number) => {
  activeFaena.value = index
  const content = document.querySelector('.faena-content')
  if (content) {
    content.scrollIntoView({ behavior: 'smooth', block: 'nearest' })
  }
}

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
  if (currentFaena.value) {
    currentImageIndex.value = (currentImageIndex.value + 1) % currentFaena.value.fotos.length
  }
}

const prevImage = () => {
  if (currentFaena.value) {
    currentImageIndex.value =
      (currentImageIndex.value - 1 + currentFaena.value.fotos.length) %
      currentFaena.value.fotos.length
  }
}
</script>

<style scoped>
.service-details {
  padding: 100px 0;
  background: linear-gradient(135deg, rgba(26, 40, 66, 0.03) 0%, rgba(255, 255, 255, 1) 100%);
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Header */
.section-header {
  text-align: center;
  margin-bottom: 60px;
}

.header-badge {
  display: inline-block;
  padding: 8px 24px;
  background: var(--color-red);
  color: white;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 2px;
  border-radius: 4px;
  margin-bottom: 20px;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 800;
  color: var(--color-navy);
  margin-bottom: 15px;
}

.title-line {
  width: 80px;
  height: 4px;
  background: var(--color-red);
  margin: 0 auto 25px;
  border-radius: 2px;
}

.section-subtitle {
  font-size: 1.1rem;
  color: var(--color-text);
  max-width: 700px;
  margin: 0 auto;
  line-height: 1.7;
}

/* Tabs */
.tabs-container {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 50px;
}

.tab-button {
  padding: 14px 28px;
  background: white;
  border: 2px solid rgba(26, 40, 66, 0.1);
  color: var(--color-navy);
  font-weight: 600;
  font-size: 0.95rem;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.tab-button:hover {
  border-color: var(--color-red);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(227, 30, 36, 0.15);
}

.tab-button.active {
  background: var(--color-red);
  color: white;
  border-color: var(--color-red);
}

/* Faena Content */
.faena-content {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.08);
}

.faena-header {
  background: linear-gradient(135deg, var(--color-navy) 0%, rgba(26, 40, 66, 0.9) 100%);
  padding: 40px;
  color: white;
}

.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 30px;
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 20px;
  backdrop-filter: blur(10px);
}

.status-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #4ade80;
}

.status-badge.completed .status-dot {
  background: #94a3b8;
}

.faena-title {
  font-size: 2.2rem;
  font-weight: 800;
  margin-bottom: 15px;
}

.location {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 1rem;
  opacity: 0.9;
}

.location svg {
  width: 20px;
  height: 20px;
  stroke: white;
}

/* Info Grid */
.faena-info {
  padding: 40px;
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
  margin-bottom: 40px;
}

.info-item {
  display: flex;
  gap: 16px;
  padding: 20px;
  background: linear-gradient(135deg, rgba(26, 40, 66, 0.03) 0%, rgba(255, 255, 255, 1) 100%);
  border-radius: 12px;
  border: 1px solid rgba(26, 40, 66, 0.08);
  transition: all 0.3s ease;
}

.info-item:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
  border-color: var(--color-red);
}

.info-item svg {
  width: 24px;
  height: 24px;
  stroke: var(--color-red);
  stroke-width: 2;
  flex-shrink: 0;
  margin-top: 4px;
}

.info-item div {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.info-item .label {
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: var(--color-navy);
  opacity: 0.7;
}

.info-item .value {
  font-size: 1rem;
  font-weight: 600;
  color: var(--color-navy);
  line-height: 1.4;
}

/* Sections */
.description,
.indicadores,
.dotacion,
.equipamiento,
.alcance,
.fortalezas,
.servicios {
  margin-bottom: 40px;
}

.description h4,
.indicadores h4,
.dotacion h4,
.equipamiento h4,
.alcance h4,
.fortalezas h4,
.servicios h4 {
  font-size: 1.4rem;
  font-weight: 700;
  color: var(--color-navy);
  margin-bottom: 20px;
  padding-bottom: 12px;
  border-bottom: 3px solid var(--color-red);
  display: inline-block;
}

.description p {
  font-size: 1.05rem;
  line-height: 1.8;
  color: var(--color-text);
}

.indicadores ul,
.dotacion ul,
.equipamiento ul,
.alcance ul,
.fortalezas ul,
.servicios ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 14px;
}

.indicadores li,
.dotacion li,
.equipamiento li,
.alcance li,
.fortalezas li,
.servicios li {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  font-size: 1rem;
  line-height: 1.6;
  color: var(--color-text);
}

.indicadores li svg,
.dotacion li svg,
.equipamiento li svg,
.alcance li svg,
.fortalezas li svg,
.servicios li svg {
  width: 20px;
  height: 20px;
  stroke: var(--color-red);
  stroke-width: 2.5;
  flex-shrink: 0;
  margin-top: 2px;
}

/* Gallery */
.gallery {
  padding: 2%;
  margin-top: 50px;
  padding-top: 40px;
  border-top: 1px solid rgba(26, 40, 66, 0.1);
}

.gallery h4 {
  font-size: 1.4rem;
  font-weight: 700;
  color: var(--color-navy);
  margin-bottom: 30px;
  padding-bottom: 12px;
  border-bottom: 3px solid var(--color-red);
  display: inline-block;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.gallery-item {
  position: relative;
  aspect-ratio: 4/3;
  border-radius: 12px;
  overflow: hidden;
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: all 0.4s ease;
}

.gallery-item:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 32px rgba(227, 30, 36, 0.2);
}

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  transition: transform 0.4s ease;
  display: block;
}

.gallery-item:hover img {
  transform: scale(1.1);
}

.gallery-item .overlay {
  position: absolute;
  inset: 0;
  background: rgba(227, 30, 36, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.4s ease;
}

.gallery-item:hover .overlay {
  opacity: 1;
}

.gallery-item .overlay svg {
  width: 48px;
  height: 48px;
  stroke: white;
  stroke-width: 2;
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

/* Responsive */
@media (max-width: 1024px) {
  .section-title {
    font-size: 2rem;
  }

  .faena-title {
    font-size: 1.8rem;
  }

  .gallery-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
  }
}

@media (max-width: 768px) {
  .service-details {
    padding: 60px 0;
  }

  .section-title {
    font-size: 1.75rem;
  }

  .tabs-container {
    gap: 8px;
  }

  .tab-button {
    padding: 10px 18px;
    font-size: 0.85rem;
  }

  .faena-header {
    padding: 30px 24px;
  }

  .faena-title {
    font-size: 1.5rem;
  }

  .faena-info {
    padding: 24px;
  }

  .info-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }

  .gallery-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
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
}

@media (max-width: 480px) {
  .section-title {
    font-size: 1.5rem;
  }

  .section-subtitle {
    font-size: 0.95rem;
  }

  .tab-button {
    width: 100%;
    text-align: center;
  }
}
</style>
