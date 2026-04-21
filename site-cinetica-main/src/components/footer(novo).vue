<template>
  <footer class="app-footer">
    <div class="footer-inner">

      <!-- Brand column -->
      <div class="footer-brand">
        <p class="brand-name">Cinética</p>
        <p class="brand-tagline">Inteligência em Movimento</p>
        <p class="brand-description">
          Empresa Júnior de Engenharia e Tecnologia da UFES — conectando conhecimento acadêmico ao mundo real.
        </p>
      </div>

      <!-- Navigation columns -->
      <div class="footer-nav-group">
        <div class="footer-nav-col">
          <h3 class="nav-heading">Navegação</h3>
          <nav>
            <a href="#" class="footer-link" @click.prevent="scrollToSection('quem-somos')">Sobre nós</a>
            <router-link to="/servicos"  class="footer-link">Serviços</router-link>
            <router-link to="/portfolio" class="footer-link">Portfólio</router-link>
          </nav>
        </div>
        <div class="footer-nav-col">
          <h3 class="nav-heading">Contato</h3>
          <nav>
            <router-link to="/contato"  class="footer-link">Fale conosco</router-link>
            <router-link to="/feedback" class="footer-link">Feedback</router-link>
          </nav>
        </div>
      </div>

    </div>

    <!-- Bottom bar -->
    <div class="footer-bottom">
      <p class="footer-copy">&copy; {{ currentYear }} Cinética Júnior. Todos os direitos reservados.</p>
      <p class="footer-ufes">UFES · Vitória, ES</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter',
  computed: {
    currentYear() {
      return new Date().getFullYear()
    }
  },
  methods: {
    scrollToSection(id) {
      const el = document.getElementById(id)
      if (el) el.scrollIntoView({ behavior: 'smooth' })
    }
  }
}
</script>

<style scoped>
/* ═══════════════════════════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════════════════════════ */
.app-footer {
  --clr-brand:      #8A0808;
  --clr-cream:      #F6E8CD;
  --clr-cream-dim:  rgba(246, 232, 205, 0.55);
  --clr-cream-soft: rgba(246, 232, 205, 0.18);
  --ff-display: 'Playfair Display', Georgia, serif;
  --ff-body:    'DM Sans', 'Segoe UI', sans-serif;
  --transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);

  background: linear-gradient(160deg, #1a0303 0%, var(--clr-brand) 60%, #a00a0a 100%);
  color: var(--clr-cream);
  font-family: var(--ff-body);
}

/* ═══════════════════════════════════════════════════════════════
   INNER LAYOUT
═══════════════════════════════════════════════════════════════ */
.footer-inner {
  max-width: 1120px;
  margin: 0 auto;
  padding: 72px 32px 48px;
  display: grid;
  grid-template-columns: 1.4fr 1fr;
  gap: 64px;
  align-items: start;
  border-bottom: 1px solid var(--clr-cream-soft);
}

/* ═══════════════════════════════════════════════════════════════
   BRAND COLUMN
═══════════════════════════════════════════════════════════════ */
.brand-name {
  font-family: var(--ff-display);
  font-size: 2rem;
  font-weight: 700;
  font-style: italic;
  color: var(--clr-cream);
  margin: 0 0 6px;
  letter-spacing: -0.01em;
}

.brand-tagline {
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--clr-cream-dim);
  margin: 0 0 20px;
}

.brand-description {
  font-size: 0.9rem;
  line-height: 1.72;
  color: var(--clr-cream-dim);
  margin: 0;
  max-width: 360px;
}

/* ═══════════════════════════════════════════════════════════════
   NAV COLUMNS
═══════════════════════════════════════════════════════════════ */
.footer-nav-group {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 32px;
}

.footer-nav-col nav {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.nav-heading {
  font-size: 0.68rem;
  font-weight: 700;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--clr-cream-dim);
  margin: 0 0 20px;
}

.footer-link {
  font-size: 0.9rem;
  font-weight: 400;
  color: rgba(246, 232, 205, 0.75);
  text-decoration: none;
  transition: color var(--transition), transform var(--transition);
  display: inline-block;
}

.footer-link:hover {
  color: var(--clr-cream);
  transform: translateX(4px);
}

/* ═══════════════════════════════════════════════════════════════
   BOTTOM BAR
═══════════════════════════════════════════════════════════════ */
.footer-bottom {
  max-width: 1120px;
  margin: 0 auto;
  padding: 24px 32px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  flex-wrap: wrap;
}

.footer-copy,
.footer-ufes {
  font-size: 0.75rem;
  color: var(--clr-cream-dim);
  margin: 0;
  letter-spacing: 0.04em;
}

.footer-ufes {
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  opacity: 0.5;
}

/* ═══════════════════════════════════════════════════════════════
   RESPONSIVE
═══════════════════════════════════════════════════════════════ */
@media (max-width: 768px) {
  .footer-inner {
    grid-template-columns: 1fr;
    gap: 40px;
    padding: 56px 24px 40px;
  }

  .footer-nav-group {
    grid-template-columns: 1fr 1fr;
  }

  .brand-description { max-width: 100%; }
}

@media (max-width: 480px) {
  .footer-nav-group {
    grid-template-columns: 1fr;
    gap: 32px;
  }

  .footer-bottom {
    flex-direction: column;
    align-items: flex-start;
    padding: 20px 24px;
    gap: 6px;
  }
}
</style>
