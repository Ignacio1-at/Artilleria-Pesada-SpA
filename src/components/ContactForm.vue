<script setup lang="ts">
import { ref } from 'vue'

const formData = ref({
  nombre: '',
  email: '',
  asunto: '',
  mensaje: '',
})

const errors = ref({
  nombre: '',
  email: '',
  asunto: '',
  mensaje: '',
})

const isSubmitting = ref(false)
const submitSuccess = ref(false)

const asuntos = [
  'Operaciones Logísticas',
  'Mantenimiento Industrial',
  'Arriendo de Maquinaria',
  'Consultoría y Asesoría',
  'Otro',
]

const validateEmail = (email: string) => {
  const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  return re.test(email)
}

const validateForm = () => {
  let isValid = true
  errors.value = { nombre: '', email: '', asunto: '', mensaje: '' }

  if (!formData.value.nombre.trim()) {
    errors.value.nombre = 'El nombre es requerido'
    isValid = false
  }

  if (!formData.value.email.trim()) {
    errors.value.email = 'El correo electrónico es requerido'
    isValid = false
  } else if (!validateEmail(formData.value.email)) {
    errors.value.email = 'Ingresa un correo electrónico válido'
    isValid = false
  }

  if (!formData.value.asunto) {
    errors.value.asunto = 'Selecciona un asunto'
    isValid = false
  }

  if (!formData.value.mensaje.trim()) {
    errors.value.mensaje = 'El mensaje es requerido'
    isValid = false
  } else if (formData.value.mensaje.length < 20) {
    errors.value.mensaje = 'El mensaje debe tener al menos 20 caracteres'
    isValid = false
  }

  return isValid
}

const handleSubmit = async () => {
  if (!validateForm()) return

  isSubmitting.value = true

  try {
    const subject = encodeURIComponent(formData.value.asunto)
    const body = encodeURIComponent(
      `Nombre: ${formData.value.nombre}\n` +
        `Email: ${formData.value.email}\n\n` +
        `Mensaje:\n${formData.value.mensaje}`,
    )

    window.location.href = `mailto:victor.oyarzo@artilleriapesada.cl?subject=${subject}&body=${body}`

    setTimeout(() => {
      formData.value = {
        nombre: '',
        email: '',
        asunto: '',
        mensaje: '',
      }
      submitSuccess.value = true
      isSubmitting.value = false

      setTimeout(() => {
        submitSuccess.value = false
      }, 5000)
    }, 1000)
  } catch (error) {
    console.error('Error al enviar:', error)
    isSubmitting.value = false
  }
}

const charCount = ref(0)
const updateCharCount = () => {
  charCount.value = formData.value.mensaje.length
}
</script>

<template>
  <div class="contact-form-wrapper">
    <div class="form-header">
      <div class="form-icon-wrapper">
        <svg class="form-icon" viewBox="0 0 24 24" fill="none">
          <path
            d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
      </div>
      <h3>Envíanos un mensaje</h3>
      <p>Cuéntanos sobre tu proyecto y cómo podemos trabajar juntos</p>
    </div>

    <form @submit.prevent="handleSubmit" class="contact-form">
      <div class="form-row">
        <div class="form-group">
          <label for="nombre">
            <svg class="label-icon" viewBox="0 0 24 24" fill="none">
              <path
                d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
              <circle
                cx="12"
                cy="7"
                r="4"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
            Nombre completo
          </label>
          <input
            id="nombre"
            v-model="formData.nombre"
            type="text"
            placeholder="Tu nombre completo"
            :class="{ error: errors.nombre }"
          />
          <span v-if="errors.nombre" class="error-message">{{ errors.nombre }}</span>
        </div>

        <div class="form-group">
          <label for="email">
            <svg class="label-icon" viewBox="0 0 24 24" fill="none">
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
            Correo electrónico
          </label>
          <input
            id="email"
            v-model="formData.email"
            type="email"
            placeholder="tu@email.com"
            :class="{ error: errors.email }"
          />
          <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
        </div>
      </div>

      <div class="form-group">
        <label for="asunto">
          <svg class="label-icon" viewBox="0 0 24 24" fill="none">
            <path
              d="M20.59 13.41l-7.17 7.17a2 2 0 0 1-2.83 0L2 12V2h10l8.59 8.59a2 2 0 0 1 0 2.82z"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <line
              x1="7"
              y1="7"
              x2="7.01"
              y2="7"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
          Asunto
        </label>
        <select id="asunto" v-model="formData.asunto" :class="{ error: errors.asunto }">
          <option value="" disabled>Selecciona un tema</option>
          <option v-for="asunto in asuntos" :key="asunto" :value="asunto">
            {{ asunto }}
          </option>
        </select>
        <span v-if="errors.asunto" class="error-message">{{ errors.asunto }}</span>
      </div>

      <div class="form-group">
        <label for="mensaje">
          <svg class="label-icon" viewBox="0 0 24 24" fill="none">
            <path
              d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
          Mensaje
        </label>
        <textarea
          id="mensaje"
          v-model="formData.mensaje"
          placeholder="Cuéntanos sobre tu proyecto, objetivos, timeline y cualquier detalle importante..."
          rows="6"
          maxlength="500"
          :class="{ error: errors.mensaje }"
          @input="updateCharCount"
        ></textarea>
        <div class="textarea-footer">
          <span v-if="errors.mensaje" class="error-message">{{ errors.mensaje }}</span>
          <span class="char-count">{{ charCount }}/500</span>
        </div>
      </div>

      <button type="submit" class="submit-button" :disabled="isSubmitting">
        <span v-if="!isSubmitting && !submitSuccess">Enviar mensaje</span>
        <span v-else-if="isSubmitting">Enviando...</span>
        <span v-else>
          <svg
            width="20"
            height="20"
            viewBox="0 0 24 24"
            fill="none"
            style="display: inline; vertical-align: middle"
          >
            <polyline
              points="20 6 9 17 4 12"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
          Mensaje enviado
        </span>
      </button>

      <div v-if="submitSuccess" class="success-message">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
          <path
            d="M22 11.08V12a10 10 0 1 1-5.93-9.14"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
          <polyline
            points="22 4 12 14.01 9 11.01"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
        <span>¡Mensaje enviado con éxito! Te contactaremos pronto.</span>
      </div>
    </form>
  </div>
</template>

<style scoped>
.contact-form-wrapper {
  background: var(--color-white);
  border-radius: 20px;
  padding: 3.5rem 3rem;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  max-width: 800px;
  margin: 0 auto;
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.form-header {
  text-align: center;
  margin-bottom: 3rem;
}

.form-icon-wrapper {
  width: 90px;
  height: 90px;
  background: linear-gradient(135deg, rgba(227, 30, 36, 0.1) 0%, rgba(26, 40, 66, 0.05) 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
}

.form-icon {
  width: 45px;
  height: 45px;
  color: var(--color-red);
}

.form-header h3 {
  font-size: 2.2rem;
  color: var(--color-navy);
  margin-bottom: 0.75rem;
  font-weight: 800;
  letter-spacing: -0.5px;
}

.form-header p {
  color: var(--color-text);
  font-size: 1.05rem;
  line-height: 1.6;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.75rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.75rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 700;
  color: var(--color-navy);
  font-size: 0.95rem;
}

.label-icon {
  width: 20px;
  height: 20px;
  color: var(--color-red);
}

.form-group input,
.form-group select,
.form-group textarea {
  padding: 0.875rem 1rem;
  border: 2px solid rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  font-size: 1rem;
  font-family: inherit;
  transition: all 0.3s ease;
  background: var(--color-white);
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--color-red);
  box-shadow: 0 0 0 3px rgba(227, 30, 36, 0.1);
}

.form-group input.error,
.form-group select.error,
.form-group textarea.error {
  border-color: var(--color-red);
  background: rgba(227, 30, 36, 0.05);
}

.form-group select {
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg width='12' height='8' viewBox='0 0 12 8' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1L6 6L11 1' stroke='%23E31E24' stroke-width='2' stroke-linecap='round'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 1rem center;
  padding-right: 3rem;
}

.form-group textarea {
  resize: vertical;
  min-height: 140px;
  line-height: 1.6;
}

.textarea-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.char-count {
  font-size: 0.875rem;
  color: var(--color-text);
  font-weight: 600;
}

.error-message {
  color: var(--color-red);
  font-size: 0.875rem;
  font-weight: 600;
}

.submit-button {
  padding: 1rem 2.5rem;
  background: var(--color-red);
  color: var(--color-white);
  border: none;
  border-radius: 10px;
  font-size: 1.05rem;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(227, 30, 36, 0.3);
  margin-top: 1rem;
}

.submit-button:hover:not(:disabled) {
  background: var(--color-red-dark);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(227, 30, 36, 0.4);
}

.submit-button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.success-message {
  padding: 1.25rem 1.5rem;
  background: #d4edda;
  color: #155724;
  border-radius: 10px;
  text-align: center;
  font-weight: 600;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  border: 2px solid #c3e6cb;
}

.success-message svg {
  width: 24px;
  height: 24px;
  color: #155724;
  flex-shrink: 0;
}

/* RESPONSIVE */
@media (max-width: 768px) {
  .contact-form-wrapper {
    padding: 2.5rem 2rem;
  }

  .form-row {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .form-header h3 {
    font-size: 1.8rem;
  }

  .form-icon-wrapper {
    width: 80px;
    height: 80px;
  }

  .form-icon {
    width: 40px;
    height: 40px;
  }

  .form-header p {
    font-size: 1rem;
  }

  .contact-form {
    gap: 1.5rem;
  }
}

@media (max-width: 480px) {
  .contact-form-wrapper {
    padding: 2rem 1.5rem;
    border-radius: 16px;
  }

  .form-header h3 {
    font-size: 1.5rem;
  }

  .form-icon-wrapper {
    width: 70px;
    height: 70px;
  }

  .form-icon {
    width: 35px;
    height: 35px;
  }

  .form-header p {
    font-size: 0.95rem;
  }

  .form-group label {
    font-size: 0.9rem;
  }

  .form-group input,
  .form-group select,
  .form-group textarea {
    padding: 0.75rem 0.875rem;
    font-size: 0.95rem;
  }

  .submit-button {
    padding: 0.875rem 2rem;
    font-size: 1rem;
  }

  .success-message {
    padding: 1rem 1.25rem;
    font-size: 0.95rem;
  }
}
</style>
