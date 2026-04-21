<template>
  <div class="hero-wrapper">
    <section class="hero-section">
 
      <!-- ── LAYER 0 · CAROUSEL IMAGES (fundo, atrás de tudo) ──── -->
      <div class="carousel-bg" aria-hidden="true">
        <div class="carousel-track" :style="trackStyle">
          <div
            v-for="(img, i) in images"
            :key="i"
            class="carousel-slide"
          >
            <img :src="img" :alt="`Foto ${i + 1} da Cinética`" />
          </div>
        </div>
      </div>
 
      <!-- ── LAYER 1 · COLOR OVERLAY (escurece as fotos) ────────── -->
      <div class="color-overlay" aria-hidden="true"></div>
 
      <!-- ── LAYER 2 · GRAIN (textura sobre o overlay) ──────────── -->
      <div class="hero-grain" aria-hidden="true"></div>
 
      <!-- ── LAYER 3 · RINGS + DOTS decorativos ─────────────────── -->
      <div class="rings-container" aria-hidden="true">
        <div class="ring ring-1"></div>
        <div class="ring ring-2"></div>
        <div class="ring ring-3"></div>
      </div>
      <div class="accent-dot dot-a" aria-hidden="true"></div>
      <div class="accent-dot dot-b" aria-hidden="true"></div>
 
      <!-- ── LAYER 4 · CONTEÚDO (título, botões) ────────────────── -->
      <div class="hero-content">
        <p class="hero-eyebrow">Empresa Júnior · UFES</p>
 
        <h1 class="hero-title">
          <span class="title-line">Cinética</span>
          <span class="title-line title-italic">Júnior</span>
        </h1>
 
        <p class="hero-subtitle">Inteligência em Movimento</p>
 
        <div class="hero-actions">
          <a href="#nossos-servicos" class="hero-btn hero-btn--primary" @click.prevent="scrollDown">
            Nossos serviços
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 5v14M5 12l7 7 7-7"/></svg>
          </a>
          <router-link to="/contato" class="hero-btn hero-btn--ghost">Fale conosco</router-link>
        </div>
      </div>
 
      <!-- ── LAYER 4 · CONTROLES do carousel ────────────────────── -->
      <button
        class="carousel-btn carousel-btn--prev"
        @click="prevSlide"
        aria-label="Slide anterior"
      >
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg>
      </button>
      <button
        class="carousel-btn carousel-btn--next"
        @click="nextSlide"
        aria-label="Próximo slide"
      >
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
      </button>
 
      <!-- Indicators -->
      <div class="carousel-indicators" role="tablist">
        <button
          v-for="(img, i) in images"
          :key="i"
          :class="['indicator', { active: currentSlide === i }]"
          @click="goToSlide(i)"
          :aria-label="`Ir para slide ${i + 1}`"
          role="tab"
          :aria-selected="currentSlide === i"
        ></button>
      </div>
 
      <!-- Slide counter -->
      <div class="slide-counter">
        <span class="counter-current">{{ String(currentSlide + 1).padStart(2, '0') }}</span>
        <span class="counter-sep">/</span>
        <span class="counter-total">{{ String(images.length).padStart(2, '0') }}</span>
      </div>
 
      <!-- Scroll cue -->
      <div class="scroll-cue" aria-hidden="true">
        <div class="scroll-line"></div>
      </div>
 
    </section>
  </div>
</template>
 
<script>
import img1 from '../../assets/img/img1.jpeg'
import img2 from '../../assets/img/img2.jpeg'
import img3 from '../../assets/img/img3.jpeg'
import img4 from '../../assets/img/img4.jpeg'
 
export default {
  name: 'HeroSection',
  data() {
    return {
      images: [img1, img2, img3, img4],
      currentSlide: 0,
      autoPlayInterval: null,
      trackStyle: {
        transform: 'translateX(0%)',
        transition: 'transform 0.8s cubic-bezier(0.4, 0, 0.2, 1)'
      }
    }
  },
  mounted() {
    this.startAutoCarousel()
  },
  beforeUnmount() {
    if (this.autoPlayInterval) clearInterval(this.autoPlayInterval)
  },
  methods: {
    scrollDown() {
      const target = document.getElementById('nossos-servicos')
        || document.querySelector('.content-page')
      if (target) target.scrollIntoView({ behavior: 'smooth' })
    },
    startAutoCarousel() {
      this.autoPlayInterval = setInterval(() => this.nextSlide(), 5000)
    },
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.images.length
      this.updateTrack()
    },
    prevSlide() {
      this.currentSlide =
        this.currentSlide === 0 ? this.images.length - 1 : this.currentSlide - 1
      this.updateTrack()
    },
    goToSlide(index) {
      this.currentSlide = index
      this.updateTrack()
      /* Reset autoplay timer on manual navigation */
      clearInterval(this.autoPlayInterval)
      this.startAutoCarousel()
    },
    updateTrack() {
      this.trackStyle = {
        transform: `translateX(-${this.currentSlide * 100}%)`,
        transition: 'transform 0.8s cubic-bezier(0.4, 0, 0.2, 1)'
      }
    }
  }
}
</script>
 
<style scoped>
/* ═══════════════════════════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════════════════════════ */
.hero-wrapper {
  --clr-brand:      #8A0808;
  --clr-cream:      #F6E8CD;
  --clr-cream-dim:  rgba(246, 232, 205, 0.65);
  --ff-display: 'Playfair Display', Georgia, serif;
  --ff-body:    'DM Sans', 'Segoe UI', sans-serif;
  --transition: 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}
 
/* ═══════════════════════════════════════════════════════════════
   HERO SECTION  —  stacking context raiz
   Todas as camadas vivem aqui com z-index explícito:
     z-index 0  → .carousel-bg       (fotos)
     z-index 1  → .color-overlay     (escurecimento)
     z-index 2  → .hero-grain        (textura)
     z-index 3  → .rings-container   (anéis decorativos)
     z-index 3  → .accent-dot        (pontos decorativos)
     z-index 4  → .hero-content      (título / botões)
     z-index 4  → .carousel-btn      (setas)
     z-index 4  → .carousel-indicators
     z-index 4  → .slide-counter
     z-index 4  → .scroll-cue
═══════════════════════════════════════════════════════════════ */
.hero-section {
  position: relative;
  width: 100%;
  min-height: 88vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  padding: 80px 24px 100px;
  box-sizing: border-box;
  /* Cor de fallback caso as imagens não carreguem */
  background: #1a0303;
}
 
/* ── LAYER 0 · CAROUSEL BACKGROUND ─────────────────────────── */
.carousel-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
  overflow: hidden;
}
 
.carousel-track {
  display: flex;
  width: 100%;
  height: 100%;
}
 
.carousel-slide {
  flex: 0 0 100%;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
 
.carousel-slide img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
}
 
/* ── LAYER 1 · COLOR OVERLAY ────────────────────────────────── */
.color-overlay {
  position: absolute;
  inset: 0;
  z-index: 1;
  background: linear-gradient(
    160deg,
    rgba(26, 3, 3, 0.82) 0%,
    rgba(138, 8, 8, 0.68) 55%,
    rgba(192, 18, 18, 0.60) 100%
  );
  pointer-events: none;
}
 
/* ── LAYER 2 · GRAIN TEXTURE ────────────────────────────────── */
.hero-grain {
  position: absolute;
  inset: 0;
  z-index: 2;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  opacity: 0.45;
  pointer-events: none;
}
 
/* ── LAYER 3 · DECORATIVE RINGS ─────────────────────────────── */
.rings-container {
  position: absolute;
  inset: 0;
  z-index: 3;
  pointer-events: none;
}
 
@keyframes spin-cw  { to { transform: rotate(360deg); } }
@keyframes spin-ccw { to { transform: rotate(-360deg); } }
 
.ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid rgba(246, 232, 205, 0.1);
  top: 50%;
  left: 50%;
}
 
.ring-1 {
  width: 520px; height: 520px;
  margin-left: -260px; margin-top: -260px;
  animation: spin-cw 30s linear infinite;
}
.ring-2 {
  width: 720px; height: 720px;
  margin-left: -360px; margin-top: -360px;
  border-style: dashed;
  border-color: rgba(246, 232, 205, 0.06);
  animation: spin-ccw 45s linear infinite;
}
.ring-3 {
  width: 300px; height: 300px;
  margin-left: -150px; margin-top: -150px;
  border-width: 5px;
  border-color: rgba(246, 232, 205, 0.05);
  animation: spin-cw 20s linear infinite;
}
 
/* ── LAYER 3 · ACCENT DOTS ──────────────────────────────────── */
.accent-dot {
  position: absolute;
  border-radius: 50%;
  z-index: 3;
  pointer-events: none;
}
.dot-a {
  width: 200px; height: 200px;
  background: radial-gradient(circle, rgba(255,255,255,0.07) 0%, transparent 70%);
  top: 10%; right: 8%;
}
.dot-b {
  width: 120px; height: 120px;
  background: radial-gradient(circle, rgba(255,255,255,0.05) 0%, transparent 70%);
  bottom: 15%; left: 6%;
}
 
/* ── LAYER 4 · HERO CONTENT ─────────────────────────────────── */
.hero-content {
  position: relative;
  z-index: 4;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}
 
.hero-eyebrow {
  font-family: var(--ff-body);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--clr-cream-dim);
  margin: 0 0 24px;
}
 
.hero-title {
  font-family: var(--ff-display);
  font-size: clamp(3.5rem, 10vw, 9rem);
  font-weight: 900;
  line-height: 0.95;
  color: var(--clr-cream);
  margin: 0 0 20px;
  letter-spacing: -0.02em;
}
 
.title-line  { display: block; }
.title-italic {
  font-style: italic;
  color: rgba(246, 232, 205, 0.75);
  font-size: 0.7em;
}
 
.hero-subtitle {
  font-family: var(--ff-body);
  font-size: clamp(1rem, 2.5vw, 1.4rem);
  font-weight: 300;
  letter-spacing: 0.14em;
  color: var(--clr-cream-dim);
  margin: 0 0 48px;
  text-transform: uppercase;
}
 
.hero-actions {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
  justify-content: center;
}
 
.hero-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 13px 28px;
  border-radius: 999px;
  font-family: var(--ff-body);
  font-size: 0.88rem;
  font-weight: 600;
  text-decoration: none;
  cursor: pointer;
  transition: transform var(--transition), box-shadow var(--transition),
              background var(--transition), border-color var(--transition);
}
.hero-btn:hover  { transform: translateY(-2px); }
.hero-btn:active { transform: translateY(0); }
 
.hero-btn--primary {
  background: var(--clr-cream);
  color: var(--clr-brand);
  box-shadow: 0 4px 20px rgba(0,0,0,0.3);
}
.hero-btn--primary:hover {
  background: #fff;
  box-shadow: 0 8px 28px rgba(0,0,0,0.35);
}
 
.hero-btn--ghost {
  background: rgba(255,255,255,0.08);
  color: var(--clr-cream);
  border: 1px solid rgba(246, 232, 205, 0.3);
  backdrop-filter: blur(8px);
}
.hero-btn--ghost:hover {
  background: rgba(255,255,255,0.15);
  border-color: rgba(246, 232, 205, 0.55);
}
 
/* ── LAYER 4 · CAROUSEL CONTROLS ────────────────────────────── */
.carousel-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 4;
  background: rgba(255,255,255,0.12);
  border: 1px solid rgba(255,255,255,0.2);
  color: #fff;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background var(--transition), transform var(--transition),
              border-color var(--transition);
  backdrop-filter: blur(8px);
}
.carousel-btn:hover {
  background: rgba(255,255,255,0.28);
  border-color: rgba(255,255,255,0.45);
  transform: translateY(-50%) scale(1.08);
}
.carousel-btn--prev { left: 20px; }
.carousel-btn--next { right: 20px; }
 
/* ── LAYER 4 · INDICATORS ───────────────────────────────────── */
.carousel-indicators {
  position: absolute;
  bottom: 36px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 8px;
  z-index: 4;
}
 
.indicator {
  width: 6px;
  height: 6px;
  border-radius: 999px;
  background: rgba(255,255,255,0.35);
  border: none;
  cursor: pointer;
  padding: 0;
  transition: width var(--transition), background var(--transition);
}
.indicator.active {
  width: 24px;
  background: #fff;
}
 
/* ── LAYER 4 · SLIDE COUNTER ────────────────────────────────── */
.slide-counter {
  position: absolute;
  bottom: 32px;
  right: 24px;
  z-index: 4;
  font-family: var(--ff-body);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.08em;
  color: rgba(255,255,255,0.5);
  display: flex;
  align-items: center;
  gap: 4px;
}
.counter-current { color: #fff; }
.counter-sep      { opacity: 0.4; }
 
/* ── LAYER 4 · SCROLL CUE ───────────────────────────────────── */
.scroll-cue {
  position: absolute;
  bottom: 28px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 4;
}
 
@keyframes scroll-pulse {
  0%, 100% { transform: scaleY(0); transform-origin: top;    opacity: 0; }
  40%       { transform: scaleY(1); transform-origin: top;    opacity: 1; }
  80%       { transform: scaleY(1); transform-origin: bottom; opacity: 1; }
}
 
.scroll-line {
  width: 1px;
  height: 48px;
  background: linear-gradient(to bottom, rgba(246,232,205,0.8), transparent);
  animation: scroll-pulse 2.4s ease-in-out infinite;
}
 
/* ═══════════════════════════════════════════════════════════════
   RESPONSIVE
═══════════════════════════════════════════════════════════════ */
@media (max-width: 768px) {
  .hero-section { min-height: 75vh; padding: 64px 20px 80px; }
 
  .ring-1 { width: 340px; height: 340px; margin-left: -170px; margin-top: -170px; }
  .ring-2 { width: 480px; height: 480px; margin-left: -240px; margin-top: -240px; }
  .ring-3 { width: 200px; height: 200px; margin-left: -100px; margin-top: -100px; }
 
  .carousel-btn { width: 36px; height: 36px; }
  .carousel-btn--prev { left: 12px; }
  .carousel-btn--next { right: 12px; }
}
 
@media (max-width: 480px) {
  .hero-section   { min-height: 100svh; }
  .hero-actions   { flex-direction: column; width: 100%; max-width: 280px; }
  .hero-btn       { justify-content: center; }
  .slide-counter  { display: none; }
  .scroll-cue     { display: none; }
}
</style>