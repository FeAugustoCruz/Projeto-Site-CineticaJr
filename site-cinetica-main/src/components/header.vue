<template>
  <header class="app-header" :class="{ 'is-scrolled': isScrolled, 'menu-open': isMenuOpen }">
    <div class="header-inner">
 
      <!-- Logo -->
      <router-link to="/" class="site-logo-link" @click.native="closeMenu" aria-label="Início">
        <img
          src="../../public/imagens/logoCinetica.png"
          alt="Cinética Júnior"
          class="site-logo"
        />
      </router-link>
 
      <!-- Desktop navigation -->
      <nav class="nav-desktop" aria-label="Navegação principal">
        <a
          href="#quem-somos"
          class="nav-link"
          @click.prevent="scrollTo('quem-somos')"
        >Sobre nós</a>
        <router-link to="/servicos"  class="nav-link">Serviços</router-link>
        <router-link to="/portfolio" class="nav-link">Portfólio</router-link>
        <router-link to="/feedback"  class="nav-link">Feedback</router-link>
        <router-link to="/contato"   class="nav-link nav-link--cta">Fale conosco</router-link>
      </nav>
 
      <!-- Mobile hamburger -->
      <button
        class="hamburger"
        :class="{ 'is-open': isMenuOpen }"
        @click="toggleMenu"
        :aria-expanded="isMenuOpen"
        aria-label="Abrir menu"
      >
        <span class="bar bar-1"></span>
        <span class="bar bar-2"></span>
        <span class="bar bar-3"></span>
      </button>
 
    </div>
 
    <!-- Mobile drawer -->
    <transition name="drawer">
      <nav
        v-if="isMenuOpen"
        class="nav-mobile"
        aria-label="Menu mobile"
        @click="closeMenu"
      >
        <div class="nav-mobile-inner">
          <a
            href="#quem-somos"
            class="mobile-link"
            @click.stop.prevent="scrollTo('quem-somos')"
          >
            <span class="mobile-link-num">01</span>Sobre nós
          </a>
          <router-link to="/servicos"  class="mobile-link"><span class="mobile-link-num">02</span>Serviços</router-link>
          <router-link to="/portfolio" class="mobile-link"><span class="mobile-link-num">03</span>Portfólio</router-link>
          <router-link to="/feedback"  class="mobile-link"><span class="mobile-link-num">04</span>Feedback</router-link>
          <router-link to="/contato"   class="mobile-link mobile-link--cta"><span class="mobile-link-num">05</span>Fale conosco</router-link>
        </div>
 
        <p class="mobile-footer-note">Cinética Júnior · UFES</p>
      </nav>
    </transition>
 
    <!-- Backdrop -->
    <transition name="fade">
      <div
        v-if="isMenuOpen"
        class="backdrop"
        @click="closeMenu"
        aria-hidden="true"
      ></div>
    </transition>
 
  </header>
</template>
 
<script>
export default {
  name: 'AppHeader',
  data() {
    return {
      isMenuOpen: false,
      isScrolled: false,
    }
  },
  computed: {
    /**
     * O header só pode ser transparente na home ('/'),
     * onde o hero vermelho serve de fundo.
     * Em qualquer outra rota força o fundo sólido.
     */
    isOnHome() {
      return this.$route.path === '/'
    },
    /**
     * Fundo sólido quando: scrollou OU está fora da home.
     */
    isSolid() {
      return this.isScrolled || !this.isOnHome
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll, { passive: true })
    window.addEventListener('keydown', this.handleKeydown)
    /* Avalia imediatamente o scroll (ex: refresh no meio da página) */
    this.handleScroll()
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
    window.removeEventListener('keydown', this.handleKeydown)
  },
  watch: {
    isMenuOpen(val) {
      document.body.style.overflow = val ? 'hidden' : ''
    },
    '$route'() {
      this.closeMenu()
      /* Re-avalia scroll ao trocar de rota */
      this.handleScroll()
    }
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen
    },
    closeMenu() {
      this.isMenuOpen = false
    },
    handleScroll() {
      this.isScrolled = window.scrollY > 20
    },
    handleKeydown(e) {
      if (e.key === 'Escape') this.closeMenu()
    },
    scrollTo(sectionId) {
      this.closeMenu()
      if (this.$route.path === '/') {
        this.$nextTick(() => {
          const el = document.getElementById(sectionId)
          if (el) el.scrollIntoView({ behavior: 'smooth' })
        })
      } else {
        this.$router.push(`/#${sectionId}`)
      }
    }
  }
}
</script>
 
<style scoped>
/* ═══════════════════════════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════════════════════════ */
.app-header {
  --clr-brand:       #8A0808;
  --clr-brand-dark:  #6d0606;
  --clr-cream:       #F6E8CD;
  --clr-cream-dim:   rgba(246, 232, 205, 0.6);
  --ff-display: 'Playfair Display', Georgia, serif;
  --ff-body:    'DM Sans', 'Segoe UI', sans-serif;
  --header-h:   100px;
  --transition: 0.32s cubic-bezier(0.4, 0, 0.2, 1);
 
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  font-family: var(--ff-body);
 
  background: linear-gradient(135deg, #1a0303 0%, var(--clr-brand) 100%);
  box-shadow: 0 2px 24px rgba(0, 0, 0, 0.25);
  transition: box-shadow var(--transition);
}
 
.app-header.is-scrolled {
  box-shadow: 0 4px 32px rgba(0, 0, 0, 0.35);
}
 
/* ═══════════════════════════════════════════════════════════════
   INNER LAYOUT
═══════════════════════════════════════════════════════════════ */
.header-inner {
  max-width: 1120px;
  margin: 0 auto;
  padding: 0 28px;
  height: var(--header-h);
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}
 
/* ═══════════════════════════════════════════════════════════════
   LOGO
═══════════════════════════════════════════════════════════════ */
.site-logo-link {
  display: flex;
  align-items: center;
  flex-shrink: 0;
  text-decoration: none;
  transition: opacity var(--transition);
}
.site-logo-link:hover { opacity: 0.85; }
 
.site-logo {
  height: 44px;
  width: auto;
  display: block;
}
 
/* ═══════════════════════════════════════════════════════════════
   DESKTOP NAV
═══════════════════════════════════════════════════════════════ */
.nav-desktop {
  display: flex;
  align-items: center;
  gap: 4px;
}
 
.nav-link {
  position: relative;
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--clr-cream-dim);
  text-decoration: none;
  padding: 8px 14px;
  border-radius: 8px;
  letter-spacing: 0.02em;
  transition: color var(--transition), background var(--transition);
  white-space: nowrap;
}
 
.nav-link::after {
  content: '';
  position: absolute;
  bottom: 4px;
  left: 14px;
  right: 14px;
  height: 1px;
  background: var(--clr-cream);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform var(--transition);
}
 
.nav-link:hover,
.nav-link.router-link-active {
  color: var(--clr-cream);
}
 
.nav-link:hover::after,
.nav-link.router-link-active::after {
  transform: scaleX(1);
}
 
/* CTA pill button */
.nav-link--cta {
  background: rgba(246, 232, 205, 0.12);
  color: var(--clr-cream) !important;
  border: 1px solid rgba(246, 232, 205, 0.25);
  margin-left: 8px;
  padding: 8px 18px;
}
 
.nav-link--cta::after { display: none; }
 
.nav-link--cta:hover {
  background: rgba(246, 232, 205, 0.22);
  border-color: rgba(246, 232, 205, 0.5);
  transform: translateY(-1px);
}
 
/* ═══════════════════════════════════════════════════════════════
   HAMBURGER BUTTON
═══════════════════════════════════════════════════════════════ */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 5px;
  width: 40px;
  height: 40px;
  background: rgba(246, 232, 205, 0.1);
  border: 1px solid rgba(246, 232, 205, 0.2);
  border-radius: 10px;
  cursor: pointer;
  padding: 0;
  transition: background var(--transition), border-color var(--transition);
  flex-shrink: 0;
}
 
.hamburger:hover {
  background: rgba(246, 232, 205, 0.18);
  border-color: rgba(246, 232, 205, 0.4);
}
 
.bar {
  display: block;
  width: 18px;
  height: 1.5px;
  background: var(--clr-cream);
  border-radius: 2px;
  transition: transform var(--transition), opacity var(--transition), width var(--transition);
  transform-origin: center;
}
 
/* Animate to ✕ */
.hamburger.is-open .bar-1 {
  transform: translateY(6.5px) rotate(45deg);
}
.hamburger.is-open .bar-2 {
  opacity: 0;
  transform: scaleX(0);
}
.hamburger.is-open .bar-3 {
  transform: translateY(-6.5px) rotate(-45deg);
}
 
/* ═══════════════════════════════════════════════════════════════
   MOBILE DRAWER
═══════════════════════════════════════════════════════════════ */
.nav-mobile {
  position: fixed;
  top: var(--header-h);
  right: 0;
  width: min(320px, 85vw);
  height: calc(100dvh - var(--header-h));
  background: linear-gradient(160deg, #1a0303 0%, #7a0606 100%);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 32px 0 40px;
  z-index: 999;
  overflow-y: auto;
  box-shadow: -8px 0 40px rgba(0, 0, 0, 0.3);
}
 
.nav-mobile-inner {
  display: flex;
  flex-direction: column;
  gap: 4px;
  padding: 0 20px;
}
 
.mobile-link {
  display: flex;
  align-items: center;
  gap: 16px;
  font-size: 1.1rem;
  font-weight: 500;
  color: rgba(246, 232, 205, 0.75);
  text-decoration: none;
  padding: 16px 20px;
  border-radius: 12px;
  letter-spacing: 0.02em;
  transition: background var(--transition), color var(--transition), transform var(--transition);
}
 
.mobile-link:hover,
.mobile-link.router-link-active {
  background: rgba(246, 232, 205, 0.08);
  color: var(--clr-cream);
  transform: translateX(4px);
}
 
.mobile-link-num {
  font-size: 0.65rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  color: rgba(246, 232, 205, 0.3);
  font-variant-numeric: tabular-nums;
  min-width: 20px;
}
 
.mobile-link--cta {
  background: rgba(246, 232, 205, 0.1);
  color: var(--clr-cream) !important;
  border: 1px solid rgba(246, 232, 205, 0.2);
  margin-top: 12px;
}
 
.mobile-link--cta:hover {
  background: rgba(246, 232, 205, 0.18) !important;
}
 
.mobile-footer-note {
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: rgba(246, 232, 205, 0.25);
  text-align: center;
  padding: 0 20px;
}
 
/* ═══════════════════════════════════════════════════════════════
   BACKDROP
═══════════════════════════════════════════════════════════════ */
.backdrop {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.45);
  backdrop-filter: blur(3px);
  z-index: 998;
}
 
/* ═══════════════════════════════════════════════════════════════
   TRANSITIONS
═══════════════════════════════════════════════════════════════ */
.drawer-enter-active,
.drawer-leave-active {
  transition: transform 0.38s cubic-bezier(0.4, 0, 0.2, 1),
              opacity 0.3s ease;
}
.drawer-enter-from,
.drawer-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
 
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
 
/* ═══════════════════════════════════════════════════════════════
   RESPONSIVE — show hamburger, hide desktop nav
═══════════════════════════════════════════════════════════════ */
@media (max-width: 768px) {
  .nav-desktop { display: none; }
  .hamburger   { display: flex; }
}
 
@media (max-width: 480px) {
  .header-inner { padding: 0 18px; }
  .site-logo    { height: 38px; }
}
</style>