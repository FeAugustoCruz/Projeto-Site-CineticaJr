<template>
  <div class="contato-wrapper">
  <main class="contato-page">
 
    <!-- ── PAGE HEADER ─────────────────────────────────────────── -->
    <header class="page-header reveal">
      <p class="page-eyebrow">Cinética Júnior · UFES</p>
      <h1 class="page-title">Fale<br /><em>Conosco</em></h1>
      <p class="page-subtitle">
        Responderemos sua mensagem em até 48 horas úteis.
      </p>
    </header>
 
    <!-- ── MAIN CONTENT ────────────────────────────────────────── -->
    <div class="contato-grid">
 
      <!-- INFO PANEL -->
      <aside class="info-panel reveal" style="--delay: 60ms">
 
        <div class="info-brand">
          <h2 class="info-brand-name">Cinética Jr</h2>
          <p class="info-brand-tag">Inteligência em Movimento</p>
        </div>
 
        <ul class="contact-list">
          <li class="contact-item">
            <span class="contact-icon" aria-hidden="true">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
            </span>
            <div class="contact-detail">
              <span class="contact-label">Localização</span>
              <span class="contact-value">Alegre · ES · Brasil</span>
            </div>
          </li>
 
          <li class="contact-item">
            <span class="contact-icon" aria-hidden="true">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.64 12 19.79 19.79 0 0 1 1.15 3.38 2 2 0 0 1 3.12 1h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.09 8.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 21 16v.92z"/></svg>
            </span>
            <div class="contact-detail">
              <span class="contact-label">Telefone</span>
              <a href="tel:+5528999460521" class="contact-value contact-link">(28) 99946-0521</a>
            </div>
          </li>
 
          <li class="contact-item">
            <span class="contact-icon" aria-hidden="true">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
            </span>
            <div class="contact-detail">
              <span class="contact-label">E-mail</span>
              <a href="mailto:comercialcineticajunior@gmail.com" class="contact-value contact-link">comercialcineticajunior@gmail.com</a>
            </div>
          </li>
 
          <li class="contact-item">
            <span class="contact-icon" aria-hidden="true">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
            </span>
            <div class="contact-detail">
              <span class="contact-label">Instagram</span>
              <a href="https://instagram.com/cineticajunior" target="_blank" rel="noopener noreferrer" class="contact-value contact-link">@cineticajunior</a>
            </div>
          </li>
        </ul>
 
        <div class="info-accent" aria-hidden="true"></div>
      </aside>
 
      <!-- FORM PANEL -->
      <section class="form-panel reveal" style="--delay: 130ms">
        <form @submit.prevent="submitForm" novalidate class="contact-form">
 
          <div class="form-row">
            <!-- Nome -->
            <div class="form-group" :class="{ 'has-error': errors.nome }">
              <input
                type="text"
                id="nome"
                v-model="formData.nome"
                @blur="validateField('nome')"
                autocomplete="name"
                required
                placeholder=" "
              />
              <label for="nome">Nome <span class="required">*</span></label>
              <span class="field-error" v-if="errors.nome">{{ errors.nome }}</span>
            </div>
 
            <!-- Email -->
            <div class="form-group" :class="{ 'has-error': errors.email }">
              <input
                type="email"
                id="email"
                v-model="formData.email"
                @blur="validateField('email')"
                autocomplete="email"
                required
                placeholder=" "
              />
              <label for="email">E-mail <span class="required">*</span></label>
              <span class="field-error" v-if="errors.email">{{ errors.email }}</span>
            </div>
          </div>
 
          <!-- Como conheceu -->
          <div class="form-group">
            <input
              type="text"
              id="como-conheceu"
              v-model="formData.comoConheceu"
              placeholder=" "
            />
            <label for="como-conheceu">Como conheceu a Cinética?</label>
          </div>
 
          <!-- Mensagem -->
          <div class="form-group form-group--textarea" :class="{ 'has-error': errors.message }">
            <textarea
              id="mensagem"
              v-model="formData.message"
              @blur="validateField('message')"
              rows="5"
              required
              placeholder=" "
              maxlength="1000"
            ></textarea>
            <label for="mensagem">Mensagem <span class="required">*</span></label>
            <span class="char-count">{{ formData.message.length }} / 1000</span>
            <span class="field-error" v-if="errors.message">{{ errors.message }}</span>
          </div>
 
          <!-- Honeypot anti-spam -->
          <input type="checkbox" name="botcheck" style="display:none" tabindex="-1" autocomplete="off" />
 
          <div class="form-footer">
            <p class="form-note">
              <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
              Seus dados são tratados com total privacidade.
            </p>
            <button
              type="submit"
              class="submit-btn"
              :disabled="isSubmitting"
            >
              <span class="btn-label" v-if="!isSubmitting">
                Enviar mensagem
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
              </span>
              <span class="btn-label btn-label--loading" v-else>
                <span class="spinner" aria-hidden="true"></span>
                Enviando…
              </span>
            </button>
          </div>
 
        </form>
      </section>
 
    </div>
  </main>
 
  <!-- STATUS MODAL — unchanged API -->
  <StatusModal
    :is-visible="modal.isVisible"
    :status="modal.status"
    :title="modal.title"
    :message="modal.message"
    @close="closeModal"
  />
  </div>
</template>
 
<script>
import StatusModal from '../components/statusModal.vue'
import axios from 'axios'
 
export default {
  name: 'ContatoView',
  components: { StatusModal },
 
  data() {
    return {
      formData: {
        nome: '',
        email: '',
        comoConheceu: '',
        message: ''
      },
      errors: {
        nome: '',
        email: '',
        message: ''
      },
      isSubmitting: false,
      modal: {
        isVisible: false,
        status: 'sending',
        title: '',
        message: ''
      }
    }
  },
 
  mounted() {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add('is-visible')
            observer.unobserve(entry.target)
          }
        })
      },
      { threshold: 0.08, rootMargin: '0px 0px -40px 0px' }
    )
    this.$el.querySelectorAll('.reveal').forEach((el) => observer.observe(el))
    this._observer = observer
  },
 
  beforeUnmount() {
    if (this._observer) this._observer.disconnect()
  },
 
  methods: {
    validateField(field) {
      this.errors[field] = ''
      if (field === 'nome' && !this.formData.nome.trim()) {
        this.errors.nome = 'Por favor, informe seu nome.'
      }
      if (field === 'email') {
        if (!this.formData.email.trim()) {
          this.errors.email = 'Por favor, informe seu e-mail.'
        } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.formData.email)) {
          this.errors.email = 'Formato de e-mail inválido.'
        }
      }
      if (field === 'message' && !this.formData.message.trim()) {
        this.errors.message = 'Por favor, escreva sua mensagem.'
      }
    },
 
    validateAll() {
      ['nome', 'email', 'message'].forEach((f) => this.validateField(f))
      return !this.errors.nome && !this.errors.email && !this.errors.message
    },
 
    showModal(status, title, message) {
      this.modal = { isVisible: true, status, title, message }
    },
 
    closeModal() {
      this.modal.isVisible = false
    },
 
    /* ── API call — untouched logic ── */
    async submitForm() {
      if (this.isSubmitting) return
      if (!this.validateAll()) return
 
      this.isSubmitting = true
      this.showModal('sending', 'Enviando Mensagem', 'Por favor, aguarde enquanto processamos seu formulário.')
      const ACCESS_KEY = '66cb4f1d-ffbf-4b17-bd60-358f03b0074c'
      const ENDPOINT_DE_EMAIL = 'https://api.web3forms.com/submit'
 
      const payload = {
        ...this.formData,
        access_key: ACCESS_KEY,
        subject: `Nova mensagem de contato de ${this.formData.nome}`,
        botcheck: false
      }
 
      try {
        const response = await axios.post(ENDPOINT_DE_EMAIL, payload)
        if (response.data.success) {
          this.showModal('success', 'Sucesso!', 'Sua mensagem foi enviada! Responderemos em breve.')
          this.formData = { nome: '', email: '', comoConheceu: '', message: '' }
          this.errors  = { nome: '', email: '', message: '' }
        } else {
          this.showModal('error', 'Erro no Envio', response.data.message || 'Houve uma falha interna no envio.')
        }
      } catch (error) {
        console.error('Erro de comunicação:', error)
        this.showModal('error', 'Falha na Comunicação', 'Não foi possível conectar ao servidor de envio. Verifique sua conexão.')
      } finally {
        this.isSubmitting = false
      }
    }
  }
}
</script>
 
<style scoped>
/* wrapper neutro — corrige erro de raiz múltipla no Vue 2 */
.contato-wrapper {
  display: contents;
}
 
/* ═══════════════════════════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════════════════════════ */
.contato-page {
  --clr-brand:       #8A0808;
  --clr-brand-dark:  #6d0606;
  --clr-cream:       #F6E8CD;
  --clr-bg:          #fafaf8;
  --clr-surface:     #ffffff;
  --clr-text:        #1a1a1a;
  --clr-muted:       #6b6b6b;
  --clr-border:      #e8e3db;
  --clr-error:       #c0392b;
 
  --ff-display: 'Playfair Display', Georgia, serif;
  --ff-body:    'DM Sans', 'Segoe UI', sans-serif;
 
  --radius-sm:  8px;
  --radius-md:  14px;
  --radius-lg:  24px;
  --shadow-soft: 0 2px 16px rgba(0,0,0,0.06);
  --transition:  0.3s cubic-bezier(0.4, 0, 0.2, 1);
 
  font-family: var(--ff-body);
  background: var(--clr-bg);
  color: var(--clr-text);
  max-width: 1120px;
  margin: 0 auto;
  padding: 64px 28px 96px;
  overflow-x: hidden;
}
 
/* ═══════════════════════════════════════════════════════════════
   SCROLL REVEAL
═══════════════════════════════════════════════════════════════ */
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.65s ease-out calc(var(--delay, 0ms)),
              transform 0.65s ease-out calc(var(--delay, 0ms));
}
.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}
 
/* ═══════════════════════════════════════════════════════════════
   PAGE HEADER
═══════════════════════════════════════════════════════════════ */
.page-header { padding: 48px 0 64px; }
 
.page-eyebrow {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--clr-brand);
  margin: 0 0 18px;
}
 
.page-title {
  font-family: var(--ff-display);
  font-size: clamp(3rem, 7vw, 6rem);
  font-weight: 900;
  line-height: 1.0;
  color: var(--clr-text);
  margin: 0 0 20px;
  letter-spacing: -0.02em;
}
 
.page-title em {
  font-style: italic;
  color: var(--clr-brand);
}
 
.page-subtitle {
  font-size: 1.02rem;
  color: var(--clr-muted);
  margin: 0;
  line-height: 1.6;
}
 
/* ═══════════════════════════════════════════════════════════════
   GRID
═══════════════════════════════════════════════════════════════ */
.contato-grid {
  display: grid;
  grid-template-columns: 340px 1fr;
  gap: 36px;
  align-items: start;
}
 
/* ═══════════════════════════════════════════════════════════════
   INFO PANEL
═══════════════════════════════════════════════════════════════ */
.info-panel {
  background: linear-gradient(160deg, #1a0303 0%, var(--clr-brand) 100%);
  border-radius: var(--radius-lg);
  padding: 40px 34px 44px;
  color: var(--clr-cream);
  position: relative;
  overflow: hidden;
}
 
.info-accent {
  position: absolute;
  bottom: -56px;
  right: -56px;
  width: 180px;
  height: 180px;
  border-radius: 50%;
  background: rgba(255,255,255,0.04);
  pointer-events: none;
}
 
.info-brand {
  padding-bottom: 28px;
  border-bottom: 1px solid rgba(255,255,255,0.1);
  margin-bottom: 28px;
}
 
.info-brand-name {
  font-family: var(--ff-display);
  font-size: 1.8rem;
  font-weight: 700;
  font-style: italic;
  color: var(--clr-cream);
  margin: 0 0 6px;
}
 
.info-brand-tag {
  font-size: 0.67rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: rgba(246,232,205,0.45);
  margin: 0;
}
 
.contact-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 22px;
}
 
.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 14px;
}
 
.contact-icon {
  width: 38px;
  height: 38px;
  flex-shrink: 0;
  background: rgba(246,232,205,0.1);
  border-radius: var(--radius-sm);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--clr-cream);
  transition: background var(--transition);
}
 
.contact-item:hover .contact-icon {
  background: rgba(246,232,205,0.18);
}
 
.contact-detail {
  display: flex;
  flex-direction: column;
  gap: 3px;
}
 
.contact-label {
  font-size: 0.62rem;
  font-weight: 700;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: rgba(246,232,205,0.4);
}
 
.contact-value {
  font-size: 0.86rem;
  font-weight: 500;
  color: rgba(246,232,205,0.85);
  line-height: 1.5;
  word-break: break-word;
}
 
.contact-link {
  text-decoration: none;
  transition: color var(--transition);
}
.contact-link:hover { color: #fff; }
 
/* ═══════════════════════════════════════════════════════════════
   FORM PANEL
═══════════════════════════════════════════════════════════════ */
.form-panel {
  background: var(--clr-surface);
  border: 1px solid var(--clr-border);
  border-radius: var(--radius-lg);
  padding: 44px 40px 40px;
  box-shadow: var(--shadow-soft);
}
 
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
 
.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
 
/* ── Float-label group ── */
.form-group {
  position: relative;
}
 
.form-group input,
.form-group textarea {
  width: 100%;
  box-sizing: border-box;
  background: var(--clr-bg);
  border: 1.5px solid var(--clr-border);
  border-radius: var(--radius-md);
  padding: 22px 16px 10px;
  font-family: var(--ff-body);
  font-size: 0.95rem;
  color: var(--clr-text);
  line-height: 1.5;
  outline: none;
  -webkit-appearance: none;
  transition: border-color var(--transition), box-shadow var(--transition),
              background var(--transition);
}
 
.form-group textarea {
  resize: vertical;
  min-height: 130px;
  padding-bottom: 28px;
}
 
/* Floating label */
.form-group label {
  position: absolute;
  top: 50%;
  left: 16px;
  transform: translateY(-50%);
  font-size: 0.9rem;
  color: var(--clr-muted);
  pointer-events: none;
  transition: top var(--transition), font-size var(--transition),
              color var(--transition), transform var(--transition);
}
 
.form-group--textarea label {
  top: 20px;
  transform: none;
}
 
/* Floated state */
.form-group input:focus ~ label,
.form-group input:not(:placeholder-shown) ~ label,
.form-group textarea:focus ~ label,
.form-group textarea:not(:placeholder-shown) ~ label {
  top: 9px;
  transform: none;
  font-size: 0.66rem;
  font-weight: 700;
  letter-spacing: 0.07em;
  color: var(--clr-brand);
}
 
.form-group--textarea input:focus ~ label,
.form-group--textarea textarea:focus ~ label,
.form-group--textarea textarea:not(:placeholder-shown) ~ label {
  top: 8px;
  transform: none;
}
 
/* Focus ring */
.form-group input:focus,
.form-group textarea:focus {
  border-color: var(--clr-brand);
  background: var(--clr-surface);
  box-shadow: 0 0 0 3px rgba(138, 8, 8, 0.08);
}
 
/* Error state */
.form-group.has-error input,
.form-group.has-error textarea {
  border-color: var(--clr-error);
  box-shadow: 0 0 0 3px rgba(192, 57, 43, 0.07);
}
 
.form-group.has-error label {
  color: var(--clr-error) !important;
}
 
.field-error {
  display: block;
  font-size: 0.71rem;
  color: var(--clr-error);
  margin-top: 6px;
  padding-left: 4px;
  font-weight: 500;
}
 
.char-count {
  position: absolute;
  bottom: 10px;
  right: 14px;
  font-size: 0.64rem;
  color: var(--clr-muted);
  opacity: 0.55;
  pointer-events: none;
}
 
.required {
  color: var(--clr-brand);
  font-size: 0.8em;
}
 
/* ── Footer ── */
.form-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  flex-wrap: wrap;
  margin-top: 4px;
}
 
.form-note {
  display: flex;
  align-items: center;
  gap: 7px;
  font-size: 0.74rem;
  color: var(--clr-muted);
  margin: 0;
  opacity: 0.75;
}
 
/* ── Submit button ── */
.submit-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #1a0303 0%, var(--clr-brand) 100%);
  color: var(--clr-cream);
  font-family: var(--ff-body);
  font-size: 0.9rem;
  font-weight: 600;
  padding: 14px 30px;
  border: none;
  border-radius: 999px;
  cursor: pointer;
  letter-spacing: 0.03em;
  box-shadow: 0 4px 18px rgba(138, 8, 8, 0.28);
  transition: transform var(--transition), box-shadow var(--transition), opacity var(--transition);
  min-width: 190px;
}
 
.submit-btn:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 8px 26px rgba(138, 8, 8, 0.38);
}
 
.submit-btn:active:not(:disabled) { transform: translateY(0); }
 
.submit-btn:disabled {
  opacity: 0.72;
  cursor: not-allowed;
}
 
.btn-label {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: gap var(--transition);
}
 
.submit-btn:hover:not(:disabled) .btn-label { gap: 12px; }
 
.btn-label--loading { gap: 10px; }
 
@keyframes spin { to { transform: rotate(360deg); } }
 
.spinner {
  display: inline-block;
  width: 16px;
  height: 16px;
  border: 2px solid rgba(246,232,205,0.3);
  border-top-color: var(--clr-cream);
  border-radius: 50%;
  animation: spin 0.7s linear infinite;
  flex-shrink: 0;
}
 
/* ═══════════════════════════════════════════════════════════════
   RESPONSIVE — TABLET  ≤960px
═══════════════════════════════════════════════════════════════ */
@media (max-width: 960px) {
  .contato-grid {
    grid-template-columns: 1fr;
    gap: 28px;
  }
 
  .contact-list {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 16px 28px;
  }
 
  .info-accent { display: none; }
}
 
/* ═══════════════════════════════════════════════════════════════
   RESPONSIVE — MOBILE  ≤640px
═══════════════════════════════════════════════════════════════ */
@media (max-width: 640px) {
  .contato-page {
    padding: 36px 18px 72px;
  }
 
  .page-header { padding: 24px 0 44px; }
  .page-title  { font-size: 2.6rem; }
 
  .info-panel  { padding: 28px 22px 32px; }
 
  .contact-list {
    grid-template-columns: 1fr;
    gap: 18px;
  }
 
  .form-panel {
    padding: 28px 18px 24px;
  }
 
  .form-row {
    grid-template-columns: 1fr;
  }
 
  .form-footer {
    flex-direction: column;
    align-items: flex-start;
  }
 
  .submit-btn {
    width: 100%;
    justify-content: center;
  }
}
</style>