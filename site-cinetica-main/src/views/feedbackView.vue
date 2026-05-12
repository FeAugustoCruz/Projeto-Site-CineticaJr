<template>
  <section class="feedback-page">
 
    <!-- ── PAGE HEADER ─────────────────────────────────────────── -->
    <div class="page-header">
      <p class="page-eyebrow">O que dizem sobre nós</p>
      <h1 class="page-title">Feedback dos<br /><em>Nossos Clientes</em></h1>
      <p class="page-subtitle">
        Resultados reais de quem confiou na Cinética Jr para transformar ideias em soluções.
      </p>
    </div>
 
    <!-- ── STATS BAR ──────────────────────────────────────────── -->
    <div class="stats-bar">
      <div class="stat-item">
        <span class="stat-number">98%</span>
        <span class="stat-label">Satisfação geral</span>
      </div>
      <div class="stat-divider" aria-hidden="true"></div>
      <div class="stat-item">
        <span class="stat-number">40+</span>
        <span class="stat-label">Projetos entregues</span>
      </div>
      <div class="stat-divider" aria-hidden="true"></div>
      <div class="stat-item">
        <span class="stat-number">5★</span>
        <span class="stat-label">Avaliação média</span>
      </div>
    </div>
 
    <!-- ── CAROUSEL ───────────────────────────────────────────── -->
    <div class="carousel-wrapper">
 
      <!-- Featured card com transição -->
      <div class="carousel-stage">
        <transition :name="transitionName" mode="out-in">
          <article
            v-if="currentFeedback"
            class="feedback-card"
            :key="currentFeedback.id"
          >
            <!-- Quote mark decorativo -->
            <div class="quote-mark" aria-hidden="true">"</div>
 
            <!-- Stars -->
            <div class="stars" :aria-label="`${currentFeedback.stars} de 5 estrelas`">
              <span
                v-for="i in 5"
                :key="i"
                class="star"
                :class="{ filled: i <= currentFeedback.stars }"
                aria-hidden="true"
              >★</span>
            </div>
 
            <!-- Text -->
            <blockquote class="feedback-text">
              {{ currentFeedback.text }}
            </blockquote>
 
            <!-- Author row -->
            <footer class="feedback-author-row">
              <div class="author-avatar" :style="{ background: currentFeedback.avatarColor }">
                {{ currentFeedback.initials }}
              </div>
              <div class="author-info">
                <p class="author-name">{{ currentFeedback.author }}</p>
                <p class="author-role">{{ currentFeedback.role }}</p>
              </div>
              <div class="company-badge" v-if="currentFeedback.company">
                {{ currentFeedback.company }}
              </div>
            </footer>
          </article>
        </transition>
      </div>
 
      <!-- Controls -->
      <div class="carousel-controls">
        <button
          class="ctrl-btn"
          @click="previousFeedback"
          aria-label="Depoimento anterior"
        >
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg>
        </button>
 
        <div class="indicators">
          <button
            v-for="(fb, index) in feedbacks"
            :key="fb.id"
            class="indicator-dot"
            :class="{ active: index === currentIndex }"
            @click="goToFeedback(index)"
            :aria-label="`Ver depoimento ${index + 1}`"
            :aria-current="index === currentIndex"
          ></button>
        </div>
 
        <button
          class="ctrl-btn"
          @click="nextFeedback"
          aria-label="Próximo depoimento"
        >
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
        </button>
      </div>
 
      <!-- Counter -->
      <p class="carousel-counter">
        <span class="counter-cur">{{ String(currentIndex + 1).padStart(2, '0') }}</span>
        <span class="counter-sep"> / </span>
        <span class="counter-tot">{{ String(feedbacks.length).padStart(2, '0') }}</span>
      </p>
 
    </div>
 
    <!-- ── GRID DE CARDS SECUNDÁRIOS ──────────────────────────── -->
    <div class="cards-grid">
      <article
        v-for="(fb, i) in feedbacks"
        :key="fb.id"
        class="mini-card"
        :class="{ 'mini-card--active': i === currentIndex }"
        @click="goToFeedback(i)"
        role="button"
        :aria-label="`Ver depoimento de ${fb.author}`"
        tabindex="0"
        @keydown.enter="goToFeedback(i)"
      >
        <div class="mini-stars">
          <span v-for="j in fb.stars" :key="j" class="mini-star">★</span>
        </div>
        <p class="mini-text">"{{ fb.text.slice(0, 80) }}…"</p>
        <div class="mini-author">
          <div class="mini-avatar" :style="{ background: fb.avatarColor }">{{ fb.initials }}</div>
          <div>
            <p class="mini-name">{{ fb.author }}</p>
            <p class="mini-role">{{ fb.company || fb.role }}</p>
          </div>
        </div>
      </article>
    </div>
 
    <!-- ── CTA ────────────────────────────────────────────────── -->
    <div class="feedback-cta">
      <p class="cta-text">Quer ser nosso próximo caso de sucesso?</p>
      <router-link to="/contato" class="cta-btn">
        Fale com a Cinética
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
      </router-link>
    </div>
 
  </section>
</template>
 
<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
 
const feedbacks = ref([
  {
    id: 1,
    text: 'Estou gostando demais das tratativas e do resultado final do site. A equipe da Cinética demonstrou muito profissionalismo e comprometimento do início ao fim.',
    author: 'Pedro Henrique Brandão',
    role: 'Diretor Executivo',
    company: 'Sudeste Ambiental',
    initials: 'PH',
    avatarColor: '#2d6a4f',
    stars: 5,
  },
  {
    id: 2,
    text: 'A equipe foi extremamente profissional e entregou o projeto antes do prazo. O resultado final superou nossas expectativas em qualidade e atenção aos detalhes.',
    author: 'Camila Torres',
    role: 'CEO',
    company: 'NovaTech Soluções',
    initials: 'CT',
    avatarColor: '#1d3557',
    stars: 5,
  },
  {
    id: 3,
    text: 'Experiência fantástica desde o primeiro contato. A comunicação foi clara e eficiente em todas as etapas. O site ficou exatamente como imaginávamos. Recomendo fortemente!',
    author: 'Pedro Lemos',
    role: 'Sócio-Fundador',
    company: 'Lemos & Oliveira Consultoria',
    initials: 'LO',
    avatarColor: '#6d4c41',
    stars: 5,
  },
  {
    id: 4,
    text: 'Contratamos o Manual de Boas Práticas e ficamos impressionados com a profundidade técnica e a didática do documento. Passou na inspeção sanitária sem nenhuma ressalva.',
    author: 'Ana Beatriz Cunha',
    role: 'Gerente de Qualidade',
    company: 'Sabores da Serra Alimentos',
    initials: 'SS',
    avatarColor: '#b5451b',
    stars: 5,
  },
  {
    id: 5,
    text: 'O Jardim Filtrante entregou tudo o que prometeram — funcionalidade, estética e custo dentro do orçamento. A equipe nos acompanhou em todas as etapas da implantação.',
    author: 'Marcelo Freitas',
    role: 'Engenheiro Responsável',
    company: 'EcoVerde Projetos',
    initials: 'EV',
    avatarColor: '#386641',
    stars: 5,
  },
  {
    id: 6,
    text: 'Landing page entregue com agilidade e qualidade visual impecável. Nossas conversões aumentaram 40% no primeiro mês após o lançamento. Resultado acima do esperado.',
    author: 'Juliana Matos',
    role: 'Head de Marketing',
    company: 'Impulso Digital',
    initials: 'ID',
    avatarColor: '#7b2d8b',
    stars: 5,
  },
])
 
const currentIndex = ref(0)
const currentFeedback = computed(() => feedbacks.value[currentIndex.value])
const transitionName = ref('slide-left')
 
const AUTOPLAY_INTERVAL = 6000
let intervalId = null
 
const startAutoplay = () => {
  clearInterval(intervalId)
  intervalId = setInterval(() => nextFeedback(), AUTOPLAY_INTERVAL)
}
 
const nextFeedback = () => {
  transitionName.value = 'slide-left'
  currentIndex.value = (currentIndex.value + 1) % feedbacks.value.length
}
 
const previousFeedback = () => {
  transitionName.value = 'slide-right'
  currentIndex.value = (currentIndex.value - 1 + feedbacks.value.length) % feedbacks.value.length
  startAutoplay()
}
 
const goToFeedback = (index) => {
  transitionName.value = index > currentIndex.value ? 'slide-left' : 'slide-right'
  currentIndex.value = index
  startAutoplay()
}
 
onMounted(() => startAutoplay())
onUnmounted(() => clearInterval(intervalId))
</script>
 
<style scoped>
/* ═══════════════════════════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════════════════════════ */
.feedback-page {
  --clr-brand:       #8A0808;
  --clr-brand-dark:  #6d0606;
  --clr-brand-light: #fdf0e8;
  --clr-cream:       #F6E8CD;
  --clr-bg:          #fafaf8;
  --clr-surface:     #ffffff;
  --clr-text:        #1a1a1a;
  --clr-muted:       #6b6b6b;
  --clr-border:      #e8e3db;
  --clr-star:        #f5a623;
 
  --ff-display: 'Playfair Display', Georgia, serif;
  --ff-body:    'DM Sans', 'Segoe UI', sans-serif;
 
  --radius-md:  14px;
  --radius-lg:  24px;
  --shadow-card:  0 2px 16px rgba(0,0,0,0.06);
  --shadow-hover: 0 10px 36px rgba(0,0,0,0.11);
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
   PAGE HEADER
═══════════════════════════════════════════════════════════════ */
.page-header {
  padding: 48px 0 56px;
}
 
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
  font-size: clamp(2.8rem, 6vw, 5.5rem);
  font-weight: 900;
  line-height: 1.02;
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
  line-height: 1.65;
  max-width: 520px;
}
 
/* ═══════════════════════════════════════════════════════════════
   STATS BAR
═══════════════════════════════════════════════════════════════ */
.stats-bar {
  display: flex;
  align-items: center;
  gap: 0;
  background: var(--clr-surface);
  border: 1px solid var(--clr-border);
  border-radius: var(--radius-lg);
  padding: 28px 40px;
  margin-bottom: 64px;
  box-shadow: var(--shadow-card);
}
 
.stat-item {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  text-align: center;
}
 
.stat-number {
  font-family: var(--ff-display);
  font-size: clamp(1.8rem, 3vw, 2.6rem);
  font-weight: 900;
  color: var(--clr-brand);
  line-height: 1;
}
 
.stat-label {
  font-size: 0.75rem;
  font-weight: 500;
  color: var(--clr-muted);
  letter-spacing: 0.04em;
}
 
.stat-divider {
  width: 1px;
  height: 44px;
  background: var(--clr-border);
  flex-shrink: 0;
}
 
/* ═══════════════════════════════════════════════════════════════
   CAROUSEL WRAPPER
═══════════════════════════════════════════════════════════════ */
.carousel-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 28px;
  margin-bottom: 64px;
}
 
/* ── Carousel stage ── */
.carousel-stage {
  width: 100%;
  max-width: 780px;
  position: relative;
  overflow: hidden;
  min-height: 280px;
}
 
/* ── Featured feedback card ── */
.feedback-card {
  background: var(--clr-surface);
  border: 1px solid var(--clr-border);
  border-radius: var(--radius-lg);
  padding: 44px 44px 36px;
  position: relative;
  box-shadow: var(--shadow-card);
  width: 100%;
  box-sizing: border-box;
}
 
/* Decorative top line */
.feedback-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 44px;
  right: 44px;
  height: 3px;
  background: linear-gradient(90deg, var(--clr-brand), transparent);
  border-radius: 0 0 4px 4px;
}
 
.quote-mark {
  font-family: var(--ff-display);
  font-size: 6rem;
  line-height: 0.6;
  color: var(--clr-brand);
  opacity: 0.12;
  position: absolute;
  top: 32px;
  right: 36px;
  font-style: italic;
  pointer-events: none;
  user-select: none;
}
 
/* Stars */
.stars {
  display: flex;
  gap: 3px;
  margin-bottom: 20px;
}
 
.star {
  font-size: 1.1rem;
  color: var(--clr-border);
  transition: color var(--transition);
}
 
.star.filled {
  color: var(--clr-star);
}
 
/* Blockquote */
.feedback-text {
  font-family: var(--ff-display);
  font-size: clamp(1rem, 2vw, 1.2rem);
  font-style: italic;
  line-height: 1.72;
  color: var(--clr-text);
  margin: 0 0 32px;
  position: relative;
  z-index: 1;
}
 
/* Author row */
.feedback-author-row {
  display: flex;
  align-items: center;
  gap: 14px;
  padding-top: 22px;
  border-top: 1px solid var(--clr-border);
  margin: 0;
}
 
.author-avatar {
  width: 46px;
  height: 46px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.78rem;
  font-weight: 700;
  color: #fff;
  letter-spacing: 0.04em;
  flex-shrink: 0;
}
 
.author-info { flex: 1; }
 
.author-name {
  font-size: 0.92rem;
  font-weight: 700;
  color: var(--clr-text);
  margin: 0 0 2px;
}
 
.author-role {
  font-size: 0.75rem;
  color: var(--clr-muted);
  margin: 0;
}
 
.company-badge {
  font-size: 0.68rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--clr-brand);
  background: var(--clr-brand-light);
  border: 1px solid rgba(138,8,8,0.15);
  padding: 5px 12px;
  border-radius: 999px;
  white-space: nowrap;
  flex-shrink: 0;
}
 
/* ── Carousel controls ── */
.carousel-controls {
  display: flex;
  align-items: center;
  gap: 20px;
}
 
.ctrl-btn {
  width: 42px;
  height: 42px;
  border-radius: 50%;
  border: 1.5px solid var(--clr-border);
  background: var(--clr-surface);
  color: var(--clr-text);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: var(--shadow-card);
  transition: background var(--transition), border-color var(--transition),
              transform var(--transition), color var(--transition);
}
 
.ctrl-btn:hover {
  background: var(--clr-brand);
  border-color: var(--clr-brand);
  color: #fff;
  transform: scale(1.08);
}
 
.indicators {
  display: flex;
  gap: 8px;
}
 
.indicator-dot {
  width: 7px;
  height: 7px;
  border-radius: 999px;
  border: none;
  background: var(--clr-border);
  cursor: pointer;
  padding: 0;
  transition: width var(--transition), background var(--transition);
}
 
.indicator-dot.active {
  width: 24px;
  background: var(--clr-brand);
}
 
/* Counter */
.carousel-counter {
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.08em;
  color: var(--clr-muted);
  margin: 0;
}
 
.counter-cur { color: var(--clr-brand); font-size: 0.85rem; }
.counter-sep { opacity: 0.4; }
 
/* ═══════════════════════════════════════════════════════════════
   MINI CARDS GRID
═══════════════════════════════════════════════════════════════ */
.cards-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-bottom: 64px;
}
 
.mini-card {
  background: var(--clr-surface);
  border: 1.5px solid var(--clr-border);
  border-radius: var(--radius-md);
  padding: 22px 20px 18px;
  cursor: pointer;
  transition: box-shadow var(--transition), border-color var(--transition),
              transform var(--transition);
  display: flex;
  flex-direction: column;
  gap: 10px;
}
 
.mini-card:hover {
  box-shadow: var(--shadow-hover);
  transform: translateY(-3px);
  border-color: rgba(138,8,8,0.25);
}
 
.mini-card--active {
  border-color: var(--clr-brand);
  box-shadow: 0 0 0 3px rgba(138,8,8,0.08), var(--shadow-card);
}
 
.mini-stars {
  display: flex;
  gap: 2px;
}
 
.mini-star {
  font-size: 0.75rem;
  color: var(--clr-star);
}
 
.mini-text {
  font-size: 0.8rem;
  font-style: italic;
  color: var(--clr-muted);
  line-height: 1.6;
  margin: 0;
  flex: 1;
}
 
.mini-author {
  display: flex;
  align-items: center;
  gap: 10px;
  padding-top: 10px;
  border-top: 1px solid var(--clr-border);
}
 
.mini-avatar {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.62rem;
  font-weight: 700;
  color: #fff;
  flex-shrink: 0;
}
 
.mini-name {
  font-size: 0.78rem;
  font-weight: 700;
  color: var(--clr-text);
  margin: 0 0 1px;
}
 
.mini-role {
  font-size: 0.68rem;
  color: var(--clr-brand);
  margin: 0;
  font-weight: 600;
}
 
/* ═══════════════════════════════════════════════════════════════
   CTA
═══════════════════════════════════════════════════════════════ */
.feedback-cta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
  background: linear-gradient(135deg, #1a0303 0%, var(--clr-brand) 60%, #b81010 100%);
  border-radius: var(--radius-lg);
  padding: 36px 44px;
  flex-wrap: wrap;
}
 
.cta-text {
  font-family: var(--ff-display);
  font-size: clamp(1.1rem, 2.5vw, 1.5rem);
  font-style: italic;
  color: var(--clr-cream);
  margin: 0;
}
 
.cta-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--clr-cream);
  color: var(--clr-brand);
  font-weight: 700;
  font-size: 0.88rem;
  padding: 13px 26px;
  border-radius: 999px;
  text-decoration: none;
  white-space: nowrap;
  box-shadow: 0 4px 18px rgba(0,0,0,0.2);
  transition: background var(--transition), transform var(--transition),
              gap var(--transition), box-shadow var(--transition);
  flex-shrink: 0;
}
 
.cta-btn:hover {
  background: #fff;
  transform: translateY(-2px);
  gap: 12px;
  box-shadow: 0 8px 26px rgba(0,0,0,0.25);
}
 
/* ═══════════════════════════════════════════════════════════════
   SLIDE TRANSITIONS
═══════════════════════════════════════════════════════════════ */
.slide-left-enter-active,
.slide-left-leave-active,
.slide-right-enter-active,
.slide-right-leave-active {
  transition: opacity 0.38s ease, transform 0.38s cubic-bezier(0.4, 0, 0.2, 1);
  position: absolute;
  width: 100%;
}
 
.slide-left-enter-from  { opacity: 0; transform: translateX(40px); }
.slide-left-leave-to    { opacity: 0; transform: translateX(-40px); }
.slide-right-enter-from { opacity: 0; transform: translateX(-40px); }
.slide-right-leave-to   { opacity: 0; transform: translateX(40px); }
 
/* ═══════════════════════════════════════════════════════════════
   RESPONSIVE — TABLET ≤900px
═══════════════════════════════════════════════════════════════ */
@media (max-width: 900px) {
  .cards-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
 
/* ═══════════════════════════════════════════════════════════════
   RESPONSIVE — MOBILE ≤640px
═══════════════════════════════════════════════════════════════ */
@media (max-width: 640px) {
  .feedback-page {
    padding: 36px 18px 72px;
  }
 
  .page-header {
    padding: 28px 0 40px;
  }
 
  .stats-bar {
    padding: 20px 18px;
    gap: 0;
    border-radius: var(--radius-md);
  }
 
  .stat-number { font-size: 1.6rem; }
  .stat-label  { font-size: 0.65rem; }
  .stat-divider { height: 32px; }
 
  .feedback-card {
    padding: 28px 22px 24px;
  }
 
  .feedback-card::before {
    left: 22px;
    right: 22px;
  }
 
  .feedback-author-row {
    flex-wrap: wrap;
    gap: 10px;
  }
 
  .company-badge { order: 3; }
 
  .cards-grid {
    grid-template-columns: 1fr;
  }
 
  .feedback-cta {
    flex-direction: column;
    align-items: flex-start;
    padding: 28px 24px;
    gap: 20px;
  }
 
  .cta-btn {
    width: 100%;
    justify-content: center;
  }
}
</style>
 