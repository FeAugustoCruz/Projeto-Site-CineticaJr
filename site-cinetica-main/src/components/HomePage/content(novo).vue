<template>
  <main class="content-page">

    <!-- ── HERO SECTION ─────────────────────────────────────────── -->
    <section class="hero-section reveal-on-scroll">
      <div class="hero-eyebrow">empresa júnior · ufes</div>
      <h1 class="hero-headline">
        <span class="headline-line">O que é uma</span>
        <span class="headline-line accent">Empresa Júnior?</span>
      </h1>
      <div class="hero-body">
        <p>
          Uma Empresa Júnior é uma organização sem fins lucrativos formada e gerenciada
          por estudantes universitários, com o objetivo de aplicar na prática os
          conhecimentos adquiridos na graduação.
        </p>
        <p>
          Operam dentro das universidades, com orientação de professores e profissionais
          da área. Funcionam como uma empresa real — com CNPJ, estrutura organizacional,
          execução de serviços e cultura interna — mas oferecem soluções com valores
          abaixo do mercado.
        </p>
      </div>
      <div class="hero-badge">
        <span>Estudantes que entregam resultado</span>
      </div>
    </section>

    <!-- ── DIVIDER ───────────────────────────────────────────────── -->
    <div class="section-divider reveal-on-scroll" aria-hidden="true">
      <span class="divider-line"></span>
      <span class="divider-icon">✦</span>
      <span class="divider-line"></span>
    </div>

    <!-- ── QUEM SOMOS ────────────────────────────────────────────── -->
    <section id="quem-somos" class="info-section reveal-on-scroll">
      <div class="section-label">01 · Quem somos</div>
      <div class="info-grid">
        <div class="info-heading-col">
          <h2 class="section-heading">
            Conheça a<br />
            <em>Cinética</em>
          </h2>
        </div>
        <div class="info-text-col">
          <p>
            A Cinética é a Empresa Júnior de Engenharia e Tecnologia da UFES,
            especializada em oferecer soluções tecnológicas, industriais e ambientais
            para empresas e empreendedores.
          </p>
          <p>
            Composta por estudantes das áreas de TI e engenharia de alimentos, químicas,
            florestais e madeireira, aplicamos o conhecimento acadêmico na prática —
            desenvolvendo projetos inovadores que criam soluções tecnológicas e
            sustentáveis.
          </p>
          <div class="tag-list">
            <span class="tag">Tecnologia</span>
            <span class="tag">Engenharia</span>
            <span class="tag">Sustentabilidade</span>
            <span class="tag">Inovação</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ── DIVIDER ───────────────────────────────────────────────── -->
    <div class="section-divider reveal-on-scroll" aria-hidden="true">
      <span class="divider-line"></span>
      <span class="divider-icon">✦</span>
      <span class="divider-line"></span>
    </div>

    <!-- ── NOSSOS SERVIÇOS ───────────────────────────────────────── -->
    <section id="nossos-servicos" class="info-section reveal-on-scroll">
      <div class="section-label">02 · Nossos serviços</div>
      <div class="info-grid">
        <div class="info-heading-col">
          <h2 class="section-heading">
            Soluções que<br />
            <em>impulsionam</em>
          </h2>
        </div>
        <div class="info-text-col">
          <p>
            Oferecemos soluções integradas em Tecnologia e Engenharia para impulsionar
            seu negócio de forma completa. No ambiente digital, construímos sua presença
            online com sites de alta performance e landing pages estratégicas, focadas
            em converter visitantes em clientes.
          </p>
          <p>
            Garantimos excelência e conformidade dos seus produtos com serviços que vão
            desde implementação de soluções sustentáveis, como o Jardim Filtrante, até
            documentação técnica essencial — Manual de Boas Práticas, Rotulagem
            Nutricional e Testes de Prateleira.
          </p>
          <div class="service-cards">
            <div class="service-card">
              <div class="service-icon">💻</div>
              <span>Desenvolvimento Web</span>
            </div>
            <div class="service-card">
              <div class="service-icon">🌿</div>
              <span>Soluções Sustentáveis</span>
            </div>
            <div class="service-card">
              <div class="service-icon">📋</div>
              <span>Documentação Técnica</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ── CTA ───────────────────────────────────────────────────── -->
    <section class="cta-section reveal-on-scroll">
      <div class="cta-inner">
        <div class="cta-image-col">
          <div class="polaroid-frame">
            <div class="image-container">
              <img
                src="../../assets/img/castelinho3.jpg"
                alt="Castelinho"
                class="polaroid-image img-back"
              />
              <img
                src="../../assets/img/cici.png"
                alt="mascote"
                class="polaroid-image img-front"
              />
            </div>
            <div class="polaroid-caption">cinética · ufes</div>
          </div>
          <div class="floating-dot dot-1" aria-hidden="true"></div>
          <div class="floating-dot dot-2" aria-hidden="true"></div>
        </div>

        <div class="cta-content-col">
          <div class="cta-eyebrow">faça parte</div>
          <h2 class="cta-heading">Vem ser<br /><strong>Cinético!</strong></h2>
          <p class="cta-body">
            Serviços de qualidade abaixo do preço de mercado, feitos por estudantes
            da Universidade Federal do Espírito Santo comprometidos com a excelência.
          </p>
          <div class="cta-actions">
            <router-link to="/portfolio" class="btn btn-primary">
              Ver portfólio
              <span class="btn-arrow">→</span>
            </router-link>
            <router-link to="/contato" class="btn btn-ghost">
              Fale conosco
            </router-link>
          </div>
        </div>
      </div>
    </section>

  </main>
</template>

<script>
export default {
  name: 'ContentView',
  data() {
    return {
      observer: null,
    };
  },
  mounted() {
    const options = { root: null, rootMargin: '0px 0px -60px 0px', threshold: 0.12 };

    this.observer = new IntersectionObserver((entries) => {
      entries.forEach((entry, i) => {
        if (entry.isIntersecting) {
          /* stagger children slightly */
          setTimeout(() => {
            entry.target.classList.add('is-visible');
          }, i * 60);
          this.observer.unobserve(entry.target);
        }
      });
    }, options);

    this.$el.querySelectorAll('.reveal-on-scroll').forEach(el => {
      this.observer.observe(el);
    });

    this.scrollToHash(this.$route.hash);
  },
  beforeDestroy() {
    if (this.observer) this.observer.disconnect();
  },
  watch: {
    '$route.hash'(newHash) {
      this.scrollToHash(newHash);
    }
  },
  methods: {
    scrollToHash(hash) {
      this.$nextTick(() => {
        if (hash) {
          const el = document.getElementById(hash.substring(1));
          if (el) el.scrollIntoView({ behavior: 'smooth' });
        }
      });
    }
  }
}
</script>

<style scoped>
/* ═══════════════════════════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════════════════════════ */
:root {
  --clr-brand:       #8A0808;
  --clr-brand-dark:  #6d0606;
  --clr-brand-light: #fdf0e8;
  --clr-cream:       #F6E8CD;
  --clr-text:        #1a1a1a;
  --clr-muted:       #6b6b6b;
  --clr-border:      #e5e0d8;
  --clr-surface:     #fafaf8;

  --ff-display: 'Playfair Display', 'Georgia', serif;
  --ff-body:    'DM Sans', 'Segoe UI', sans-serif;

  --radius-sm: 6px;
  --radius-md: 14px;
  --radius-lg: 24px;

  --shadow-soft:   0 2px 16px rgba(0,0,0,0.06);
  --shadow-medium: 0 6px 32px rgba(0,0,0,0.10);
  --shadow-lift:   0 16px 48px rgba(0,0,0,0.14);

  --transition: 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}

/* ═══════════════════════════════════════════════════════════════
   FONT IMPORT
═══════════════════════════════════════════════════════════════ */
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;0,900;1,700&family=DM+Sans:wght@300;400;500;600&display=swap');

/* ═══════════════════════════════════════════════════════════════
   SCROLL REVEAL
═══════════════════════════════════════════════════════════════ */
.reveal-on-scroll {
  opacity: 0;
  transform: translateY(36px);
  transition: opacity 0.75s ease-out, transform 0.75s ease-out;
  will-change: opacity, transform;
}
.reveal-on-scroll.is-visible {
  opacity: 1;
  transform: translateY(0);
}

/* ═══════════════════════════════════════════════════════════════
   PAGE SHELL
═══════════════════════════════════════════════════════════════ */
.content-page {
  font-family: var(--ff-body);
  color: var(--clr-text);
  max-width: 1120px;
  margin: 0 auto;
  padding: 64px 24px 80px;
  overflow-x: hidden;
}

/* ═══════════════════════════════════════════════════════════════
   HERO SECTION
═══════════════════════════════════════════════════════════════ */
.hero-section {
  padding: 48px 0 56px;
  position: relative;
}

.hero-eyebrow {
  font-family: var(--ff-body);
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--clr-brand);
  margin-bottom: 20px;
}

.hero-headline {
  font-family: var(--ff-display);
  font-size: clamp(2.6rem, 6vw, 5rem);
  font-weight: 900;
  line-height: 1.08;
  margin: 0 0 32px;
  color: var(--clr-text);
}

.headline-line {
  display: block;
}

.headline-line.accent {
  color: var(--clr-brand);
  font-style: italic;
  position: relative;
}

.headline-line.accent::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -4px;
  width: 60%;
  height: 3px;
  background: var(--clr-brand);
  border-radius: 2px;
  opacity: 0.35;
}

.hero-body {
  max-width: 680px;
  margin-bottom: 36px;
}

.hero-body p {
  font-size: 1.05rem;
  line-height: 1.78;
  color: var(--clr-muted);
  margin-bottom: 18px;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--clr-brand-light);
  border: 1px solid rgba(138, 8, 8, 0.18);
  color: var(--clr-brand);
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  padding: 8px 18px;
  border-radius: 999px;
}

/* ═══════════════════════════════════════════════════════════════
   DIVIDER
═══════════════════════════════════════════════════════════════ */
.section-divider {
  display: flex;
  align-items: center;
  gap: 20px;
  margin: 24px 0;
}

.divider-line {
  flex: 1;
  height: 1px;
  background: var(--clr-border);
  transform-origin: left;
  transition: transform 1.2s cubic-bezier(0.25, 1, 0.5, 1);
  transform: scaleX(0);
}

.section-divider.is-visible .divider-line {
  transform: scaleX(1);
}

.divider-icon {
  font-size: 0.65rem;
  color: var(--clr-brand);
  opacity: 0.6;
  flex-shrink: 0;
}

/* ═══════════════════════════════════════════════════════════════
   INFO SECTIONS (Quem Somos / Nossos Serviços)
═══════════════════════════════════════════════════════════════ */
.info-section {
  padding: 56px 0;
  scroll-margin-top: 100px;
}

.section-label {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--clr-brand);
  margin-bottom: 32px;
}

.info-grid {
  display: grid;
  grid-template-columns: 1fr 1.6fr;
  gap: 56px;
  align-items: start;
}

.section-heading {
  font-family: var(--ff-display);
  font-size: clamp(1.8rem, 3.5vw, 2.8rem);
  font-weight: 700;
  line-height: 1.18;
  color: var(--clr-text);
  margin: 0;
  position: sticky;
  top: 100px;
}

.section-heading em {
  font-style: italic;
  color: var(--clr-brand);
}

.info-text-col p {
  font-size: 1rem;
  line-height: 1.8;
  color: var(--clr-muted);
  margin-bottom: 18px;
}

/* Tags */
.tag-list {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 28px;
}

.tag {
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.05em;
  padding: 6px 14px;
  border-radius: 999px;
  border: 1px solid var(--clr-border);
  color: var(--clr-muted);
  background: var(--clr-surface);
  transition: border-color var(--transition), color var(--transition), background var(--transition);
}

.tag:hover {
  border-color: var(--clr-brand);
  color: var(--clr-brand);
  background: var(--clr-brand-light);
}

/* Service cards */
.service-cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin-top: 32px;
}

.service-card {
  background: var(--clr-surface);
  border: 1px solid var(--clr-border);
  border-radius: var(--radius-md);
  padding: 20px 14px;
  text-align: center;
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--clr-muted);
  transition: box-shadow var(--transition), border-color var(--transition), transform var(--transition);
  cursor: default;
}

.service-card:hover {
  box-shadow: var(--shadow-medium);
  border-color: rgba(138, 8, 8, 0.25);
  transform: translateY(-3px);
}

.service-icon {
  font-size: 1.5rem;
  margin-bottom: 8px;
}

/* ═══════════════════════════════════════════════════════════════
   CTA SECTION
═══════════════════════════════════════════════════════════════ */
.cta-section {
  padding: 72px 0 0;
}

.cta-inner {
  background: linear-gradient(135deg, #1a0303 0%, var(--clr-brand) 60%, #b81010 100%);
  border-radius: var(--radius-lg);
  padding: 64px 56px;
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 64px;
  align-items: center;
  position: relative;
  overflow: hidden;
}

/* Decorative background shapes */
.cta-inner::before {
  content: '';
  position: absolute;
  top: -80px;
  right: -80px;
  width: 320px;
  height: 320px;
  border-radius: 50%;
  background: rgba(255,255,255,0.04);
  pointer-events: none;
}

.cta-inner::after {
  content: '';
  position: absolute;
  bottom: -60px;
  left: 30%;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background: rgba(255,255,255,0.03);
  pointer-events: none;
}

/* Polaroid */
.cta-image-col {
  position: relative;
  flex-shrink: 0;
}

.polaroid-frame {
  background: #fff;
  padding: 16px 16px 44px;
  border-radius: var(--radius-sm);
  box-shadow: var(--shadow-lift);
  transform: rotate(-3deg);
  transition: transform var(--transition);
  position: relative;
  z-index: 2;
}

.polaroid-frame:hover {
  transform: rotate(0deg) translateY(-6px);
  box-shadow: 0 24px 60px rgba(0,0,0,0.3);
}

.image-container {
  position: relative;
  width: 220px;
  height: 220px;
  background: #e8e0d6;
  border-radius: 2px;
  overflow: hidden;
}

.polaroid-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: transform 0.4s ease;
}

.img-back {
  z-index: 1;
  object-fit: cover;
  transform: rotate(2deg) scale(1.05);
}

.img-front {
  z-index: 2;
  width: 68%;
  height: 68%;
  object-fit: contain;
  top: 0; bottom: 0; left: 0; right: 0;
  margin: auto;
  transform: rotate(-4deg);
}

.polaroid-frame:hover .img-back  { transform: rotate(0deg) scale(1.08); }
.polaroid-frame:hover .img-front { transform: rotate(0deg) scale(1.06); }

.polaroid-caption {
  position: absolute;
  bottom: 12px;
  left: 0; right: 0;
  text-align: center;
  font-family: var(--ff-display);
  font-size: 0.7rem;
  font-style: italic;
  color: #999;
  letter-spacing: 0.06em;
}

/* Floating decorative dots */
.floating-dot {
  position: absolute;
  border-radius: 50%;
  opacity: 0.5;
  pointer-events: none;
}

.dot-1 {
  width: 48px;
  height: 48px;
  background: rgba(246, 232, 205, 0.3);
  top: -16px;
  left: -20px;
  z-index: 1;
}

.dot-2 {
  width: 24px;
  height: 24px;
  background: rgba(246, 232, 205, 0.2);
  bottom: 30px;
  right: -12px;
  z-index: 1;
}

/* CTA text */
.cta-eyebrow {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: rgba(31, 30, 29, 0.65);
  margin-bottom: 14px;
}

.cta-heading {
  font-family: var(--ff-display);
  font-size: clamp(2rem, 4vw, 3.4rem);
  font-weight: 700;
  line-height: 1.1;
  color: #030303;
  margin: 0 0 20px;
}

.cta-heading strong {
  font-style: italic;
  color: var(--clr-cream);
}

.cta-body {
  font-size: 0.98rem;
  line-height: 1.72;
  color: rgba(0, 0, 0, 0.8);
  margin-bottom: 36px;
  max-width: 420px;
}

.cta-actions {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}

/* Buttons */
.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 12px 26px;
  border-radius: 999px;
  font-family: var(--ff-body);
  font-size: 0.88rem;
  font-weight: 600;
  text-decoration: none;
  transition: transform var(--transition), box-shadow var(--transition),
              background var(--transition), color var(--transition);
  cursor: pointer;
}

.btn:hover { transform: translateY(-2px); }
.btn:active { transform: translateY(0); }

.btn-primary {
  background: #fff;
  color: var(--clr-brand);
  box-shadow: 0 4px 16px rgba(0,0,0,0.2);
}

.btn-primary:hover {
  background: var(--clr-cream);
  box-shadow: 0 8px 24px rgba(0,0,0,0.25);
}

.btn-arrow {
  transition: transform var(--transition);
}
.btn-primary:hover .btn-arrow { transform: translateX(3px); }

.btn-ghost {
  background: rgba(255,255,255,0.1);
  color: rgba(246, 232, 205, 0.9);
  border: 1px solid rgba(255,255,255,0.25);
  backdrop-filter: blur(4px);
}

.btn-ghost:hover {
  background: rgba(255,255,255,0.18);
  border-color: rgba(255,255,255,0.45);
}

/* ═══════════════════════════════════════════════════════════════
   RESPONSIVENESS — TABLET
═══════════════════════════════════════════════════════════════ */
@media (max-width: 960px) {
  .info-grid {
    grid-template-columns: 1fr;
    gap: 28px;
  }

  .section-heading {
    position: static;
    font-size: 2rem;
  }

  .service-cards {
    grid-template-columns: repeat(3, 1fr);
  }

  .cta-inner {
    grid-template-columns: 1fr;
    padding: 48px 40px;
    gap: 40px;
  }

  .cta-image-col {
    display: flex;
    justify-content: center;
  }
}

/* ═══════════════════════════════════════════════════════════════
   RESPONSIVENESS — MOBILE
═══════════════════════════════════════════════════════════════ */
@media (max-width: 640px) {
  .content-page {
    padding: 32px 18px 56px;
  }

  .hero-section { padding: 24px 0 40px; }
  .info-section  { padding: 40px 0; }

  .hero-headline {
    font-size: 2.2rem;
  }

  .service-cards {
    grid-template-columns: 1fr;
    gap: 10px;
  }

  .service-card {
    display: flex;
    align-items: center;
    gap: 14px;
    text-align: left;
    padding: 14px 18px;
  }

  .service-icon { margin-bottom: 0; }

  .cta-inner {
    padding: 40px 24px 48px;
    border-radius: var(--radius-md);
  }

  .image-container {
    width: 180px;
    height: 180px;
  }

  .cta-actions {
    flex-direction: column;
  }

  .btn {
    justify-content: center;
    width: 100%;
  }
}
</style>
