<template>
  <div class="home-view">
    <HeroSection />
    <ContentView />
    <AppFooter />
  </div>
</template>

<script>
import HeroSection from '../components/HomePage/HeroSection(novo).vue'
import ContentView from '../components/HomePage/content(novo).vue'
import AppFooter    from '../components/footer(novo).vue'

export default {
  name: 'HomeView',
  components: {
    HeroSection,
    ContentView,
    AppFooter
  }
}
</script>

<style>
/* ═══════════════════════════════════════════════════════════════
   GLOBAL FONT IMPORT
   Load once here — all components inherit.
═══════════════════════════════════════════════════════════════ */
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;0,900;1,700&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500;9..40,600&display=swap');

/* ═══════════════════════════════════════════════════════════════
   GLOBAL RESET & BASE
═══════════════════════════════════════════════════════════════ */
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  scroll-behavior: smooth;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
}

body {
  font-family: 'DM Sans', 'Segoe UI', sans-serif;
  background-color: #fafaf8;
  color: #1a1a1a;
  line-height: 1.6;
  overflow-x: hidden;
}

/* Remove default margin/padding from main landmark */
main {
  text-align: left;
}

/* ═══════════════════════════════════════════════════════════════
   GLOBAL SCROLLBAR (optional subtle styling)
═══════════════════════════════════════════════════════════════ */
::-webkit-scrollbar {
  width: 6px;
}
::-webkit-scrollbar-track {
  background: #f0ece4;
}
::-webkit-scrollbar-thumb {
  background: #a58d83;
  border-radius: 3px;
}
::-webkit-scrollbar-thumb:hover {
  background: #8A0808;
}

/* ═══════════════════════════════════════════════════════════════
   HOME VIEW WRAPPER
   Ensures full-width sections with no horizontal overflow.
═══════════════════════════════════════════════════════════════ */
.home-view {
  width: 100%;
  overflow-x: hidden;
}
</style>
