<template>
  <div class="hero-wrapper">
 
    <!-- ════════════════════════════════════════════════════════════
         HERO SECTION
    ════════════════════════════════════════════════════════════ -->
    <section class="hero-section">
 
      <!-- LAYER 0 · CAROUSEL IMAGES (fundo) -->
      <div class="carousel-bg" aria-hidden="true">
        <div class="carousel-track" :style="bgTrackStyle">
          <div v-for="(img, i) in bgImages" :key="i" class="carousel-slide">
            <img :src="img" :alt="`Foto ${i + 1} da Cinética`" />
          </div>
        </div>
      </div>
 
      <!-- LAYER 1 · COLOR OVERLAY -->
      <div class="color-overlay" aria-hidden="true"></div>
 
      <!-- LAYER 2 · GRAIN -->
      <div class="hero-grain" aria-hidden="true"></div>
 
      <!-- LAYER 3 · RINGS + DOTS -->
      <div class="rings-container" aria-hidden="true">
        <div class="ring ring-1"></div>
        <div class="ring ring-2"></div>
        <div class="ring ring-3"></div>
      </div>
      <div class="accent-dot dot-a" aria-hidden="true"></div>
      <div class="accent-dot dot-b" aria-hidden="true"></div>
 
      <!-- LAYER 4 · CONTEÚDO -->
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
 
      <!-- LAYER 4 · BG CAROUSEL CONTROLS -->
      <button class="carousel-btn carousel-btn--prev" @click="bgPrev" aria-label="Slide anterior">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg>
      </button>
      <button class="carousel-btn carousel-btn--next" @click="bgNext" aria-label="Próximo slide">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
      </button>
 
      <div class="carousel-indicators" role="tablist">
        <button
          v-for="(img, i) in bgImages" :key="i"
          :class="['indicator', { active: bgSlide === i }]"
          @click="bgGoTo(i)"
          :aria-label="`Ir para slide ${i + 1}`"
          role="tab" :aria-selected="bgSlide === i"
        ></button>
      </div>
 
      <div class="slide-counter">
        <span class="counter-current">{{ String(bgSlide + 1).padStart(2, '0') }}</span>
        <span class="counter-sep">/</span>
        <span class="counter-total">{{ String(bgImages.length).padStart(2, '0') }}</span>
      </div>
 
      <div class="scroll-cue" aria-hidden="true">
        <div class="scroll-line"></div>
      </div>
 
    </section>
 
    <!-- ════════════════════════════════════════════════════════════
         SEÇÃO EQUIPE
    ════════════════════════════════════════════════════════════ -->
    <section class="team-section">
      <div class="team-inner">
 
        <!-- Texto / legenda -->
        <div class="team-text">
          <p class="team-eyebrow">Nossa equipe</p>
          <h2 class="team-heading">
            Unidos e<br /><em>Proativos</em>
          </h2>
          <p class="team-description">
            A Cinética Jr é formada por estudantes que acreditam que
            <strong>fazer junto é fazer melhor</strong>. Nossa equipe combina
            iniciativa, diversidade de áreas do conhecimento e espírito
            coletivo para entregar projetos que fazem a diferença — dentro
            da universidade e além dela.
          </p>
          <ul class="team-pillars">
            <li>
              <span><strong>União</strong> — time que se apoia em cada desafio</span>
            </li>
            <li>
              <span><strong>Proatividade</strong> — soluções antes dos problemas</span>
            </li>
            <li>
              <span><strong>Aprendizado</strong> — academia aplicada ao mundo real</span>
            </li>
          </ul>
        </div>
 
        <!-- Carousel de fotos da equipe -->
        <div class="team-carousel-wrap">
          <div class="team-carousel">
 
            <div class="team-track" :style="teamTrackStyle">
              <div v-for="(item, i) in teamSlides" :key="i" class="team-slide">
                <img :src="item.src" :alt="item.alt" />
              </div>
            </div>
 
            <!-- Setas -->
            <button class="team-btn team-btn--prev" @click="teamPrev" aria-label="Foto anterior">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg>
            </button>
            <button class="team-btn team-btn--next" @click="teamNext" aria-label="Próxima foto">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"/></svg>
            </button>
 
            <!-- Caption animado -->
            <transition name="caption-fade" mode="out-in">
              <div class="team-caption" :key="teamSlide">
                {{ teamSlides[teamSlide].caption }}
              </div>
            </transition>
 
          </div>
 
          <!-- Indicadores -->
          <div class="team-indicators">
            <button
              v-for="(item, i) in teamSlides" :key="i"
              :class="['team-dot', { active: teamSlide === i }]"
              @click="teamGoTo(i)"
              :aria-label="`Ver foto ${i + 1}`"
            ></button>
          </div>
 
          <p class="team-counter">
            <span class="tc-cur">{{ String(teamSlide + 1).padStart(2, '0') }}</span>
            <span class="tc-sep"> / </span>
            <span class="tc-tot">{{ String(teamSlides.length).padStart(2, '0') }}</span>
          </p>
        </div>
 
      </div>
    </section>
 
  </div>
</template>
 
<script>
import img1 from '../../assets/img/img1.jpeg'
import img2 from '../../assets/img/img2.jpeg'
import img3 from '../../assets/img/img3.jpeg'
import img4 from '../../assets/img/img4.jpeg'
import img5 from '../../assets/img/img5.jpg'
import img6 from '../../assets/img/img6.jpg'
import img7 from '../../assets/img/img7.jpg'
import img8 from '../../assets/img/img8.jpg'
 
export default {
  name: 'HeroSection',
  data() {
    return {
      /* ── Carousel de fundo do hero ── */
      bgImages: [img1, img2, img3, img4],
      bgSlide: 0,
      bgInterval: null,
      bgTrackStyle: {
        transform: 'translateX(0%)',
        transition: 'transform 0.8s cubic-bezier(0.4, 0, 0.2, 1)'
      },
 
      /* ── Carousel da equipe ── */
      teamSlides: [
        {
          src: img5,
          alt: 'Equipe Cinética Jr no evento Juniores',
          caption: 'Representando a Cinética Jr no maior evento de Empresas Juniores do Brasil 🇧🇷'
        },
        {
          src: img6,
          alt: 'Membros da Cinética com bandeira',
          caption: 'Orgulho de vestir a camisa e carregar a bandeira da nossa EJ 🔴'
        },
        {
          src: img7,
          alt: 'Equipe Cinética em congresso nacional',
          caption: 'Conectando ideias e pessoas — porque o movimento começa aqui 🤝'
        },
        {
          src: img8,
          alt: 'Presidente da Cinética Jr com polegar positivo',
          caption: 'Liderança com energia: nosso time está sempre pronto pra mais! ⚡'
        }
      ],
      teamSlide: 0,
      teamInterval: null,
      teamTrackStyle: {
        transform: 'translateX(0%)',
        transition: 'transform 0.7s cubic-bezier(0.4, 0, 0.2, 1)'
      }
    }
  },
  mounted() {
    this.bgStartAuto()
    this.teamStartAuto()
  },
  beforeUnmount() {
    clearInterval(this.bgInterval)
    clearInterval(this.teamInterval)
  },
  methods: {
    /* ── Scroll suave ── */
    scrollDown() {
      const target = document.getElementById('nossos-servicos')
        || document.querySelector('.content-page')
      if (target) target.scrollIntoView({ behavior: 'smooth' })
    },
 
    /* ── BG carousel ── */
    bgStartAuto() {
      this.bgInterval = setInterval(() => this.bgNext(), 5000)
    },
    bgNext() {
      this.bgSlide = (this.bgSlide + 1) % this.bgImages.length
      this.bgUpdate()
    },
    bgPrev() {
      this.bgSlide = this.bgSlide === 0 ? this.bgImages.length - 1 : this.bgSlide - 1
      this.bgUpdate()
    },
    bgGoTo(i) {
      this.bgSlide = i
      this.bgUpdate()
      clearInterval(this.bgInterval)
      this.bgStartAuto()
    },
    bgUpdate() {
      this.bgTrackStyle = {
        transform: `translateX(-${this.bgSlide * 100}%)`,
        transition: 'transform 0.8s cubic-bezier(0.4, 0, 0.2, 1)'
      }
    },
 
    /* ── Team carousel ── */
    teamStartAuto() {
      this.teamInterval = setInterval(() => this.teamNext(), 4000)
    },
    teamNext() {
      this.teamSlide = (this.teamSlide + 1) % this.teamSlides.length
      this.teamUpdate()
    },
    teamPrev() {
      this.teamSlide = this.teamSlide === 0 ? this.teamSlides.length - 1 : this.teamSlide - 1
      this.teamUpdate()
    },
    teamGoTo(i) {
      this.teamSlide = i
      this.teamUpdate()
      clearInterval(this.teamInterval)
      this.teamStartAuto()
    },
    teamUpdate() {
      this.teamTrackStyle = {
        transform: `translateX(-${this.teamSlide * 100}%)`,
        transition: 'transform 0.7s cubic-bezier(0.4, 0, 0.2, 1)'
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
  --clr-bg:         #fafaf8;
  --clr-text:       #1a1a1a;
  --clr-muted:      #6b6b6b;
  --clr-border:     #e5e0d8;
  --ff-display: 'Playfair Display', Georgia, serif;
  --ff-body:    'DM Sans', 'Segoe UI', sans-serif;
  --transition: 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}
 
/* ═══════════════════════════════════════════════════════════════
   HERO  —  z-index stack:
   0 carousel-bg | 1 color-overlay | 2 grain | 3 rings/dots | 4 content
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
  background: #1a0303;
}
 
/* LAYER 0 */
.carousel-bg { position: absolute; inset: 0; z-index: 0; overflow: hidden; }
.carousel-track { display: flex; width: 100%; height: 100%; }
.carousel-slide { flex: 0 0 100%; width: 100%; height: 100%; overflow: hidden; }
.carousel-slide img { width: 100%; height: 100%; object-fit: cover; object-position: center; display: block; }
 
/* LAYER 1 */
.color-overlay {
  position: absolute; inset: 0; z-index: 1; pointer-events: none;
  background: linear-gradient(160deg, rgba(26,3,3,0.82) 0%, rgba(138,8,8,0.68) 55%, rgba(192,18,18,0.60) 100%);
}
 
/* LAYER 2 */
.hero-grain {
  position: absolute; inset: 0; z-index: 2; pointer-events: none; opacity: 0.45;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
}
 
/* LAYER 3 */
.rings-container { position: absolute; inset: 0; z-index: 3; pointer-events: none; }
@keyframes spin-cw  { to { transform: rotate(360deg);  } }
@keyframes spin-ccw { to { transform: rotate(-360deg); } }
.ring { position: absolute; border-radius: 50%; border: 1px solid rgba(246,232,205,0.1); top: 50%; left: 50%; }
.ring-1 { width: 520px; height: 520px; margin: -260px 0 0 -260px; animation: spin-cw 30s linear infinite; }
.ring-2 { width: 720px; height: 720px; margin: -360px 0 0 -360px; border-style: dashed; border-color: rgba(246,232,205,0.06); animation: spin-ccw 45s linear infinite; }
.ring-3 { width: 300px; height: 300px; margin: -150px 0 0 -150px; border-width: 5px; border-color: rgba(246,232,205,0.05); animation: spin-cw 20s linear infinite; }
.accent-dot { position: absolute; border-radius: 50%; z-index: 3; pointer-events: none; }
.dot-a { width: 200px; height: 200px; background: radial-gradient(circle, rgba(255,255,255,0.07) 0%, transparent 70%); top: 10%; right: 8%; }
.dot-b { width: 120px; height: 120px; background: radial-gradient(circle, rgba(255,255,255,0.05) 0%, transparent 70%); bottom: 15%; left: 6%; }
 
/* LAYER 4 — conteúdo */
.hero-content { position: relative; z-index: 4; text-align: center; display: flex; flex-direction: column; align-items: center; }
.hero-eyebrow { font-family: var(--ff-body); font-size: 0.72rem; font-weight: 600; letter-spacing: 0.22em; text-transform: uppercase; color: var(--clr-cream-dim); margin: 0 0 24px; }
.hero-title { font-family: var(--ff-display); font-size: clamp(3.5rem, 10vw, 9rem); font-weight: 900; line-height: 0.95; color: var(--clr-cream); margin: 0 0 20px; letter-spacing: -0.02em; }
.title-line { display: block; }
.title-italic { font-style: italic; color: rgba(246,232,205,0.75); font-size: 0.7em; }
.hero-subtitle { font-family: var(--ff-body); font-size: clamp(1rem, 2.5vw, 1.4rem); font-weight: 300; letter-spacing: 0.14em; color: var(--clr-cream-dim); margin: 0 0 48px; text-transform: uppercase; }
.hero-actions { display: flex; gap: 14px; flex-wrap: wrap; justify-content: center; }
.hero-btn { display: inline-flex; align-items: center; gap: 8px; padding: 13px 28px; border-radius: 999px; font-family: var(--ff-body); font-size: 0.88rem; font-weight: 600; text-decoration: none; cursor: pointer; transition: transform var(--transition), box-shadow var(--transition), background var(--transition), border-color var(--transition); }
.hero-btn:hover  { transform: translateY(-2px); }
.hero-btn:active { transform: translateY(0); }
.hero-btn--primary { background: var(--clr-cream); color: var(--clr-brand); box-shadow: 0 4px 20px rgba(0,0,0,0.3); }
.hero-btn--primary:hover { background: #fff; box-shadow: 0 8px 28px rgba(0,0,0,0.35); }
.hero-btn--ghost { background: rgba(255,255,255,0.08); color: var(--clr-cream); border: 1px solid rgba(246,232,205,0.3); backdrop-filter: blur(8px); }
.hero-btn--ghost:hover { background: rgba(255,255,255,0.15); border-color: rgba(246,232,205,0.55); }
 
/* LAYER 4 — bg carousel controls */
.carousel-btn { position: absolute; top: 50%; transform: translateY(-50%); z-index: 4; background: rgba(255,255,255,0.12); border: 1px solid rgba(255,255,255,0.2); color: #fff; width: 44px; height: 44px; border-radius: 50%; cursor: pointer; display: flex; align-items: center; justify-content: center; transition: background var(--transition), transform var(--transition), border-color var(--transition); backdrop-filter: blur(8px); }
.carousel-btn:hover { background: rgba(255,255,255,0.28); border-color: rgba(255,255,255,0.45); transform: translateY(-50%) scale(1.08); }
.carousel-btn--prev { left: 20px; }
.carousel-btn--next { right: 20px; }
.carousel-indicators { position: absolute; bottom: 36px; left: 50%; transform: translateX(-50%); display: flex; gap: 8px; z-index: 4; }
.indicator { width: 6px; height: 6px; border-radius: 999px; background: rgba(255,255,255,0.35); border: none; cursor: pointer; padding: 0; transition: width var(--transition), background var(--transition); }
.indicator.active { width: 24px; background: #fff; }
.slide-counter { position: absolute; bottom: 32px; right: 24px; z-index: 4; font-family: var(--ff-body); font-size: 0.72rem; font-weight: 600; letter-spacing: 0.08em; color: rgba(255,255,255,0.5); display: flex; align-items: center; gap: 4px; }
.counter-current { color: #fff; }
.counter-sep { opacity: 0.4; }
.scroll-cue { position: absolute; bottom: 28px; left: 50%; transform: translateX(-50%); z-index: 4; }
@keyframes scroll-pulse {
  0%, 100% { transform: scaleY(0); transform-origin: top;    opacity: 0; }
  40%       { transform: scaleY(1); transform-origin: top;    opacity: 1; }
  80%       { transform: scaleY(1); transform-origin: bottom; opacity: 1; }
}
.scroll-line { width: 1px; height: 48px; background: linear-gradient(to bottom, rgba(246,232,205,0.8), transparent); animation: scroll-pulse 2.4s ease-in-out infinite; }
 
/* ═══════════════════════════════════════════════════════════════
   TEAM SECTION
═══════════════════════════════════════════════════════════════ */
.team-section {
  background: var(--clr-bg);
  padding: 88px 24px;
  box-sizing: border-box;
}
 
.team-inner {
  max-width: 1120px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 72px;
  align-items: center;
}
 
/* ── Texto ── */
.team-eyebrow {
  font-family: var(--ff-body);
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--clr-brand);
  margin: 0 0 16px;
}
 
.team-heading {
  font-family: var(--ff-display);
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 700;
  line-height: 1.12;
  color: var(--clr-text);
  margin: 0 0 20px;
}
 
.team-heading em {
  font-style: italic;
  color: var(--clr-brand);
}
 
.team-description {
  font-family: var(--ff-body);
  font-size: 0.98rem;
  line-height: 1.8;
  color: var(--clr-muted);
  margin: 0 0 28px;
}
 
.team-description strong {
  color: var(--clr-text);
  font-weight: 600;
}
 
.team-pillars {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 14px;
}
 
.team-pillars li {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  font-family: var(--ff-body);
  font-size: 0.9rem;
  color: var(--clr-muted);
  line-height: 1.5;
}
 
.pillar-icon {
  font-size: 1.1rem;
  flex-shrink: 0;
  margin-top: 1px;
}
 
.team-pillars strong {
  color: var(--clr-text);
  font-weight: 600;
}
 
/* ── Carousel da equipe ── */
.team-carousel-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
}
 
.team-carousel {
  position: relative;
  width: 100%;
  max-width: 500px;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 12px 48px rgba(0,0,0,0.13);
  background: #111;
  aspect-ratio: 4 / 3;
}
 
.team-track {
  display: flex;
  width: 100%;
  height: 100%;
}
 
.team-slide {
  flex: 0 0 100%;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
 
.team-slide img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center top;
  display: block;
}
 
/* Setas */
.team-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 5;
  width: 38px;
  height: 38px;
  border-radius: 50%;
  border: 1px solid rgba(255,255,255,0.25);
  background: rgba(26,3,3,0.55);
  color: #fff;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  backdrop-filter: blur(6px);
  transition: background var(--transition), transform var(--transition), border-color var(--transition);
}
.team-btn:hover {
  background: rgba(138,8,8,0.8);
  border-color: rgba(255,255,255,0.5);
  transform: translateY(-50%) scale(1.1);
}
.team-btn--prev { left: 14px; }
.team-btn--next { right: 14px; }
 
/* Caption com fade */
.team-caption {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 40px 18px 16px;
  font-family: var(--ff-body);
  font-size: 0.8rem;
  font-weight: 500;
  color: #fff;
  text-align: center;
  line-height: 1.55;
  background: linear-gradient(to top, rgba(26,3,3,0.88) 0%, transparent 100%);
  z-index: 4;
}
 
.caption-fade-enter-active,
.caption-fade-leave-active {
  transition: opacity 0.35s ease, transform 0.35s ease;
}
.caption-fade-enter-from { opacity: 0; transform: translateY(8px); }
.caption-fade-leave-to   { opacity: 0; transform: translateY(-6px); }
 
/* Indicadores */
.team-indicators {
  display: flex;
  gap: 8px;
  justify-content: center;
}
 
.team-dot {
  width: 7px;
  height: 7px;
  border-radius: 999px;
  border: none;
  background: var(--clr-border);
  cursor: pointer;
  padding: 0;
  transition: width var(--transition), background var(--transition);
}
.team-dot.active {
  width: 22px;
  background: var(--clr-brand);
}
 
/* Contador */
.team-counter {
  font-family: var(--ff-body);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.08em;
  color: var(--clr-muted);
  margin: 0;
}
.tc-cur { color: var(--clr-brand); }
.tc-sep { opacity: 0.4; }
 
/* ═══════════════════════════════════════════════════════════════
   RESPONSIVIDADE
═══════════════════════════════════════════════════════════════ */
@media (max-width: 900px) {
  .team-inner {
    grid-template-columns: 1fr;
    gap: 48px;
  }
  .team-carousel-wrap {
    order: -1;    /* foto aparece acima do texto no tablet/mobile */
  }
  .team-carousel {
    max-width: 100%;
  }
}
 
@media (max-width: 768px) {
  .hero-section { min-height: 75vh; padding: 64px 20px 80px; }
  .ring-1 { width: 340px; height: 340px; margin: -170px 0 0 -170px; }
  .ring-2 { width: 480px; height: 480px; margin: -240px 0 0 -240px; }
  .ring-3 { width: 200px; height: 200px; margin: -100px 0 0 -100px; }
  .carousel-btn { width: 36px; height: 36px; }
  .carousel-btn--prev { left: 12px; }
  .carousel-btn--next { right: 12px; }
  .team-section { padding: 64px 20px; }
}
 
@media (max-width: 480px) {
  .hero-section    { min-height: 100svh; }
  .hero-actions    { flex-direction: column; width: 100%; max-width: 280px; }
  .hero-btn        { justify-content: center; }
  .slide-counter   { display: none; }
  .scroll-cue      { display: none; }
  .team-section    { padding: 48px 16px; }
  .team-heading    { font-size: 1.8rem; }
}
</style>