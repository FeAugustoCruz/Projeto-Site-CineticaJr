<template>
  <main class="servicos-page">
 
    <!-- ── PAGE HEADER ─────────────────────────────────────────── -->
    <header class="page-header">
      <div class="page-header-inner">
        <p class="page-eyebrow">Cinética Júnior · UFES</p>
        <h1 class="page-title">Nossos<br /><em>Serviços</em></h1>
        <p class="page-subtitle">
          Soluções integradas em Tecnologia e Engenharia com qualidade
          acadêmica e preço acessível.
        </p>
      </div>
      <!-- Decorative vertical line -->
      <div class="header-rule" aria-hidden="true"></div>
    </header>
 
    <!-- ── TECNOLOGIA ──────────────────────────────────────────── -->
    <section class="category-section">
      <div class="category-header reveal">
        <span class="category-number">01</span>
        <div class="category-label-group">
          <h2 class="category-title">Diretoria de Tecnologia</h2>
          <p class="category-desc">Presença digital de alto desempenho para o seu negócio</p>
        </div>
      </div>
 
      <div class="services-grid">
 
        <!-- Landing Page -->
        <article class="service-card reveal" style="--delay: 0ms">
          <div class="card-top">
            <div class="card-icon">🖥️</div>
            <span class="card-badge card-badge--price">R$ 1.500</span>
          </div>
          <h3 class="card-title">Landing Page</h3>
          <p class="card-body">
            Página desenvolvida estrategicamente para converter visitantes em
            clientes, guiando-os a uma ação específica. Design atrativo,
            conteúdo persuasivo e estrutura otimizada para resultados.
          </p>
          <div class="card-footer">
            <router-link to="/contato" class="card-cta">
              Solicitar proposta
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
            </router-link>
          </div>
        </article>
 
        <!-- Desenvolvimento Web -->
        <article class="service-card service-card--featured reveal" style="--delay: 80ms">
          <div class="card-top">
            <div class="card-icon">⚙️</div>
            <span class="card-badge card-badge--quote">Sob consulta</span>
          </div>
          <h3 class="card-title">Desenvolvimento Web</h3>
          <p class="card-body">
            Criação, manutenção e otimização de sites e sistemas online com
            presença digital eficiente, segura e de alto desempenho — do
            front-end interativo ao back-end e banco de dados.
          </p>
          <div class="card-footer">
            <router-link to="/contato" class="card-cta card-cta--filled">
              Realizar orçamento
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
            </router-link>
          </div>
        </article>
 
      </div>
    </section>
 
    <!-- ── DIVIDER ─────────────────────────────────────────────── -->
    <div class="section-divider reveal" aria-hidden="true">
      <span class="divider-line"></span>
      <span class="divider-gem">✦</span>
      <span class="divider-line"></span>
    </div>
 
    <!-- ── ENGENHARIA ──────────────────────────────────────────── -->
    <section class="category-section">
      <div class="category-header reveal">
        <span class="category-number">02</span>
        <div class="category-label-group">
          <h2 class="category-title">Diretoria de Engenharia</h2>
          <p class="category-desc">Qualidade, conformidade e sustentabilidade para seus produtos</p>
        </div>
      </div>
 
      <div class="services-grid services-grid--wide">
 
        <!-- Jardim Filtrante -->
        <article class="service-card reveal" style="--delay: 0ms">
          <div class="card-top">
            <div class="card-icon">🌿</div>
            <span class="card-badge card-badge--price">R$ 1.500</span>
          </div>
          <h3 class="card-title">Jardim Filtrante</h3>
          <p class="card-body">
            Sistema natural de tratamento de águas residuais com plantas e
            substratos. Solução sustentável, de baixo custo, que remove
            impurezas e valoriza paisagisticamente o espaço.
          </p>
          <div class="card-footer">
            <router-link to="/contato" class="card-cta">
              Solicitar proposta
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
            </router-link>
          </div>
        </article>
 
        <!-- Manual de Boas Práticas -->
        <article class="service-card reveal" style="--delay: 70ms">
          <div class="card-top">
            <div class="card-icon">📋</div>
            <span class="card-badge card-badge--price">R$ 1.500</span>
          </div>
          <h3 class="card-title">Manual de Boas Práticas</h3>
          <p class="card-body">
            Documento essencial (BPF) que estabelece padrões de higiene,
            armazenamento e produção conforme normas sanitárias — reduzindo
            riscos de contaminação e problemas com fiscalização.
          </p>
          <div class="card-footer">
            <router-link to="/contato" class="card-cta">
              Solicitar proposta
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
            </router-link>
          </div>
        </article>
 
        <!-- Rotulagem Nutricional -->
        <article class="service-card reveal" style="--delay: 140ms">
          <div class="card-top">
            <div class="card-icon">🏷️</div>
            <span class="card-badge card-badge--price">R$ 1.500</span>
          </div>
          <h3 class="card-title">Rotulagem Nutricional</h3>
          <p class="card-body">
            Conformidade com exigências da ANVISA: calorias, macronutrientes,
            fibras, sódio e alegações nutricionais. Transmite credibilidade
            e mantém sua marca dentro da legislação vigente.
          </p>
          <div class="card-footer">
            <router-link to="/contato" class="card-cta">
              Solicitar proposta
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
            </router-link>
          </div>
        </article>
 
        <!-- Teste de Prateleira -->
        <article class="service-card reveal" style="--delay: 210ms">
          <div class="card-top">
            <div class="card-icon">🔬</div>
            <span class="card-badge card-badge--price">R$ 1.500</span>
          </div>
          <h3 class="card-title">Teste de Prateleira</h3>
          <p class="card-body">
            Avaliação da vida útil e estabilidade dos seus produtos,
            garantindo segurança alimentar, qualidade consistente e
            conformidade com as exigências regulatórias do setor.
          </p>
          <div class="card-footer">
            <router-link to="/contato" class="card-cta">
              Solicitar proposta
              <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
            </router-link>
          </div>
        </article>
 
      </div>
    </section>
 
    <!-- ── CTA FINAL ───────────────────────────────────────────── -->
    <section class="cta-strip reveal">
      <div class="cta-strip-inner">
        <div class="cta-strip-text">
          <p class="cta-strip-eyebrow">Pronto para começar?</p>
          <h2 class="cta-strip-heading">Fale com nossa equipe de vendas</h2>
          <p class="cta-strip-sub">
            Estudantes da UFES entregando soluções reais com qualidade e preço justo.
          </p>
        </div>
        <router-link to="/contato" class="cta-strip-btn">
          Entrar em contato
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
        </router-link>
      </div>
    </section>
 
  </main>
</template>
 
<script>
export default {
  name: 'ServicosView',
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
      { threshold: 0.1, rootMargin: '0px 0px -48px 0px' }
    )
    this.$el.querySelectorAll('.reveal').forEach((el) => observer.observe(el))
    this._observer = observer
  },
  beforeUnmount() {
    if (this._observer) this._observer.disconnect()
  }
}
</script>
 
<style scoped>
/* ═══════════════════════════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════════════════════════ */
.servicos-page {
  --clr-brand:        #8A0808;
  --clr-brand-dark:   #6d0606;
  --clr-brand-light:  #fdf0e8;
  --clr-cream:        #F6E8CD;
  --clr-bg:           #fafaf8;
  --clr-surface:      #ffffff;
  --clr-text:         #1a1a1a;
  --clr-muted:        #6b6b6b;
  --clr-border:       #e8e3db;
 
  --ff-display: 'Playfair Display', Georgia, serif;
  --ff-body:    'DM Sans', 'Segoe UI', sans-serif;
 
  --radius-md: 16px;
  --radius-lg: 24px;
  --shadow-card:  0 2px 16px rgba(0,0,0,0.06);
  --shadow-hover: 0 12px 40px rgba(0,0,0,0.11);
  --transition:   0.32s cubic-bezier(0.4, 0, 0.2, 1);
 
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
  transform: translateY(28px);
  transition: opacity 0.65s ease-out calc(var(--delay, 0ms)),
              transform 0.65s ease-out calc(var(--delay, 0ms));
  will-change: opacity, transform;
}
.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
}
 
/* ═══════════════════════════════════════════════════════════════
   PAGE HEADER
═══════════════════════════════════════════════════════════════ */
.page-header {
  padding: 48px 0 72px;
  position: relative;
}
 
.page-eyebrow {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--clr-brand);
  margin: 0 0 20px;
}
 
.page-title {
  font-family: var(--ff-display);
  font-size: clamp(3rem, 7vw, 6rem);
  font-weight: 900;
  line-height: 1.0;
  color: var(--clr-text);
  margin: 0 0 24px;
  letter-spacing: -0.02em;
}
 
.page-title em {
  font-style: italic;
  color: var(--clr-brand);
}
 
.page-subtitle {
  font-size: 1.05rem;
  line-height: 1.72;
  color: var(--clr-muted);
  max-width: 520px;
  margin: 0;
}
 
.header-rule {
  position: absolute;
  right: 0;
  top: 48px;
  bottom: 0;
  width: 1px;
  background: linear-gradient(to bottom, var(--clr-brand), transparent);
  opacity: 0.2;
}
 
/* ═══════════════════════════════════════════════════════════════
   CATEGORY HEADER
═══════════════════════════════════════════════════════════════ */
.category-section {
  margin-bottom: 64px;
}
 
.category-header {
  display: flex;
  align-items: flex-start;
  gap: 24px;
  margin-bottom: 36px;
  padding-bottom: 24px;
  border-bottom: 1px solid var(--clr-border);
}
 
.category-number {
  font-family: var(--ff-display);
  font-size: 3rem;
  font-weight: 900;
  font-style: italic;
  color: var(--clr-brand);
  opacity: 0.18;
  line-height: 1;
  flex-shrink: 0;
  margin-top: 2px;
}
 
.category-title {
  font-family: var(--ff-display);
  font-size: clamp(1.6rem, 3vw, 2.2rem);
  font-weight: 700;
  color: var(--clr-text);
  margin: 0 0 6px;
  letter-spacing: -0.01em;
}
 
.category-desc {
  font-size: 0.88rem;
  color: var(--clr-muted);
  margin: 0;
  line-height: 1.5;
}
 
/* ═══════════════════════════════════════════════════════════════
   SERVICES GRID
═══════════════════════════════════════════════════════════════ */
.services-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}
 
.services-grid--wide {
  grid-template-columns: repeat(2, 1fr);
}
 
/* ═══════════════════════════════════════════════════════════════
   SERVICE CARD
═══════════════════════════════════════════════════════════════ */
.service-card {
  background: var(--clr-surface);
  border: 1px solid var(--clr-border);
  border-radius: var(--radius-lg);
  padding: 28px 28px 24px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  box-shadow: var(--shadow-card);
  transition: box-shadow var(--transition), transform var(--transition),
              border-color var(--transition);
  position: relative;
  overflow: hidden;
}
 
.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: var(--clr-brand);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform var(--transition);
  border-radius: var(--radius-lg) var(--radius-lg) 0 0;
}
 
.service-card:hover {
  box-shadow: var(--shadow-hover);
  transform: translateY(-4px);
  border-color: rgba(138, 8, 8, 0.2);
}
 
.service-card:hover::before {
  transform: scaleX(1);
}
 
/* Featured card */
.service-card--featured {
  background: linear-gradient(145deg, #1a0303 0%, var(--clr-brand) 100%);
  border-color: transparent;
  color: var(--clr-cream);
}
 
.service-card--featured::before {
  background: rgba(246, 232, 205, 0.5);
}
 
.service-card--featured .card-title {
  color: #fff;
}
 
.service-card--featured .card-body {
  color: rgba(246, 232, 205, 0.75);
}
 
.service-card--featured:hover {
  border-color: transparent;
}
 
/* Card top row */
.card-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
}
 
.card-icon {
  font-size: 1.6rem;
  line-height: 1;
}
 
/* Badge */
.card-badge {
  font-family: var(--ff-body);
  font-size: 0.72rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  padding: 5px 12px;
  border-radius: 999px;
  white-space: nowrap;
}
 
.card-badge--price {
  background: var(--clr-brand-light);
  color: var(--clr-brand);
  border: 1px solid rgba(138, 8, 8, 0.15);
}
 
.card-badge--quote {
  background: rgba(255,255,255,0.12);
  color: rgba(246, 232, 205, 0.85);
  border: 1px solid rgba(255,255,255,0.2);
}
 
/* Card text */
.card-title {
  font-family: var(--ff-display);
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--clr-text);
  margin: 0;
  line-height: 1.3;
}
 
.card-body {
  font-size: 0.88rem;
  line-height: 1.75;
  color: var(--clr-muted);
  margin: 0;
  flex: 1;
}
 
/* Card footer */
.card-footer {
  margin-top: 8px;
  padding-top: 16px;
  border-top: 1px solid var(--clr-border);
}
 
.service-card--featured .card-footer {
  border-top-color: rgba(255,255,255,0.12);
}
 
/* CTA link */
.card-cta {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--clr-brand);
  text-decoration: none;
  letter-spacing: 0.03em;
  transition: gap var(--transition), color var(--transition);
}
 
.card-cta:hover {
  gap: 10px;
  color: var(--clr-brand-dark);
}
 
/* Filled CTA (for featured card) */
.card-cta--filled {
  background: var(--clr-cream);
  color: var(--clr-brand);
  padding: 10px 20px;
  border-radius: 999px;
  font-size: 0.82rem;
  box-shadow: 0 4px 14px rgba(0,0,0,0.18);
  transition: background var(--transition), transform var(--transition),
              box-shadow var(--transition), gap var(--transition);
}
 
.card-cta--filled:hover {
  background: #fff;
  transform: translateY(-1px);
  box-shadow: 0 6px 20px rgba(0,0,0,0.22);
  color: var(--clr-brand-dark);
}
 
/* ═══════════════════════════════════════════════════════════════
   SECTION DIVIDER
═══════════════════════════════════════════════════════════════ */
.section-divider {
  display: flex;
  align-items: center;
  gap: 20px;
  margin: 8px 0 72px;
}
 
.divider-line {
  flex: 1;
  height: 1px;
  background: var(--clr-border);
}
 
.divider-gem {
  font-size: 0.6rem;
  color: var(--clr-brand);
  opacity: 0.5;
  flex-shrink: 0;
}
 
/* ═══════════════════════════════════════════════════════════════
   CTA STRIP
═══════════════════════════════════════════════════════════════ */
.cta-strip {
  margin-top: 32px;
  border-radius: var(--radius-lg);
  background: linear-gradient(135deg, #1a0303 0%, var(--clr-brand) 60%, #b81010 100%);
  overflow: hidden;
  position: relative;
}
 
.cta-strip::after {
  content: '';
  position: absolute;
  top: -80px;
  right: -80px;
  width: 280px;
  height: 280px;
  border-radius: 50%;
  background: rgba(255,255,255,0.04);
  pointer-events: none;
}
 
.cta-strip-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
  padding: 52px 48px;
  flex-wrap: wrap;
}
 
.cta-strip-eyebrow {
  font-size: 0.68rem;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(246, 232, 205, 0.55);
  margin: 0 0 10px;
}
 
.cta-strip-heading {
  font-family: var(--ff-display);
  font-size: clamp(1.4rem, 3vw, 2rem);
  font-weight: 700;
  color: #fff;
  margin: 0 0 10px;
  line-height: 1.2;
}
 
.cta-strip-sub {
  font-size: 0.9rem;
  color: rgba(246, 232, 205, 0.65);
  margin: 0;
  line-height: 1.6;
  max-width: 420px;
}
 
.cta-strip-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: var(--clr-cream);
  color: var(--clr-brand);
  font-weight: 700;
  font-size: 0.9rem;
  padding: 14px 28px;
  border-radius: 999px;
  text-decoration: none;
  white-space: nowrap;
  box-shadow: 0 4px 20px rgba(0,0,0,0.22);
  transition: background var(--transition), transform var(--transition),
              box-shadow var(--transition), gap var(--transition);
  flex-shrink: 0;
  position: relative;
  z-index: 1;
}
 
.cta-strip-btn:hover {
  background: #fff;
  transform: translateY(-2px);
  box-shadow: 0 8px 28px rgba(0,0,0,0.28);
  gap: 14px;
}
 
/* ═══════════════════════════════════════════════════════════════
   RESPONSIVE
═══════════════════════════════════════════════════════════════ */
@media (max-width: 860px) {
  .services-grid,
  .services-grid--wide {
    grid-template-columns: 1fr;
  }
}
 
@media (max-width: 768px) {
  .servicos-page {
    padding: 40px 20px 72px;
  }
 
  .page-header {
    padding: 32px 0 56px;
  }
 
  .header-rule { display: none; }
 
  .category-header {
    flex-direction: column;
    gap: 8px;
  }
 
  .category-number {
    font-size: 2rem;
  }
 
  .cta-strip-inner {
    flex-direction: column;
    align-items: flex-start;
    padding: 40px 28px;
    gap: 28px;
  }
 
  .cta-strip-btn {
    width: 100%;
    justify-content: center;
  }
}
 
@media (max-width: 480px) {
  .service-card {
    padding: 22px 20px 18px;
  }
 
  .page-title {
    font-size: 2.6rem;
  }
}
</style>