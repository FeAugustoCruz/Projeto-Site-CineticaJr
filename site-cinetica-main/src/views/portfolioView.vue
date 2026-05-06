<template>
  <section id="projects" class="portfolio-page">
 
    <!-- Header -->
    <div class="section-header">
      <span class="section-label">Trabalhos Selecionados</span>
      <h2 class="section-title">Portfólio</h2>
      <p class="section-subtitle">
        Projetos desenvolvidos com foco em experiência, performance e design.
      </p>
    </div>
 
    <!-- Cards Grid -->
    <div class="projects-grid">
      <article
        v-for="(project, index) in projects"
        :key="project.id"
        class="project-card"
        :style="{ '--delay': index * 100 + 'ms' }"
      >
        <!-- Image -->
        <div  class="card-image-wrap">
          <img :src="project.image" :alt="project.title" class="card-image" />
          <div class="card-image-overlay">
            <a :href="project.demourl" target="_blank" class="overlay-btn">
              <svg  width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/>
              </svg>
              Visualizar
            </a>
          </div>
        </div>
 
        <!-- Content -->
        <div class="card-body">
 
          <!-- Tags -->
          <div class="card-meta">
            <span v-for="(tag, i) in project.tags" :key="i" class="tag">{{ tag }}</span>
          </div>
 
          <!-- Title + Description -->
          <h3 class="card-title">{{ project.title }}</h3>
          <p class="card-description">{{ project.description }}</p>
 
          <!-- Footer -->
          <div class="card-footer">
            <a
              v-if="project.demourl"
              :href="project.demourl"
              target="_blank"
              class="btn-visualizar"
            >
              <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/>
                <polyline points="15 3 21 3 21 9"/>
                <line x1="10" y1="14" x2="21" y2="3"/>
              </svg>
              Visualizar
            </a>
            <span class="card-index">{{ String(index + 1).padStart(2, '0') }}</span>
          </div>
 
        </div>
      </article>
    </div>
 
  </section>
</template>
 
<script setup>
import img1 from '../assets/img/sudeste.png'
import img2 from '../assets/img/famaalegre.png'
import img3 from '../assets/img/riverguard.png'
 
const projects = [
  {
    id: 1,
    title: "Sudeste Ambiental",
    description:
      "Site institucional para consultoria ambiental e geologia. Apresenta serviços de licenciamento, remediação e hidrogeologia com identidade visual sólida e navegação clara.",
    image: img1,
    tags: ["Vue.js", "Tailwind CSS", "Vite", "Lovable"],
    demourl: "https://sudeste.lovable.app/",
  },
  {
    id: 2,
    title: "FamaAlegre FM",
    description:
      "Plataforma web para rádio FM 104,5 com player ao vivo, programação interativa, chat em tempo real e painel de promoções para engajamento da audiência.",
    image: img2,
    tags: ["React", "TypeScript", "Supabase", "Lovable"],
    demourl: "https://fame-alegre-connect.lovable.app/",
  },
  {
    id: 3,
    title: "RiverGuard Pulse",
    description:
      "Dashboard de monitoramento hidrológico em tempo real para a Defesa Civil. Exibe níveis do rio, alertas de transbordamento, sensores ativos e protocolos de emergência.",
    image: img3,
    tags: ["React", "TypeScript", "Recharts", "Lovable"],
    demourl: "https://riverguard-pulse.lovable.app/",
  },
]
</script>
 
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,300&display=swap');
 
/* ── Variables ── */
:root {
  --cream:       #f6e8cd;
  --red:         #8a0808;
  --red-dark:    #5f0606;
  --red-light:   rgba(138, 8, 8, 0.07);
  --red-glow:    rgba(138, 8, 8, 0.18);
  --ink:         #1a1008;
  --ink-soft:    #8a7060;
  --border:      rgba(138, 8, 8, 0.10);
  --white:       #ffffff;
  --shadow-sm:   0 2px 16px rgba(26, 16, 8, 0.06);
  --shadow-lg:   0 24px 64px rgba(26, 16, 8, 0.17);
  --radius-card: 28px;
  --radius-img:  20px;
}
 
/* ── Page ── */
.portfolio-page {
  background-color: var(--cream);
  padding: clamp(60px, 8vw, 120px) clamp(20px, 5vw, 80px);
  font-family: 'DM Sans', sans-serif;
  min-height: 100vh;
}
 
/* ── Header ── */
.section-header {
  max-width: 540px;
  margin: 0 0 clamp(48px, 6vw, 88px);
}
 
.section-label {
  display: inline-block;
  font-size: 0.68rem;
  font-weight: 600;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--red);
  background: var(--red-light);
  border: 1px solid var(--border);
  padding: 5px 16px;
  border-radius: 100px;
  margin-bottom: 22px;
}
 
.section-title {
  font-family: 'Playfair Display', Georgia, serif;
  font-size: clamp(2.4rem, 5vw, 3.8rem);
  font-weight: 700;
  color: var(--ink);
  line-height: 1.1;
  margin: 0 0 14px;
  letter-spacing: -0.025em;
}
 
.section-subtitle {
  font-size: 0.98rem;
  color: var(--ink-soft);
  line-height: 1.65;
  font-weight: 300;
  margin: 0;
}
 
/* ── Grid ── */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: clamp(20px, 2.5vw, 36px);
  max-width: 1360px;
}
 
/* ── Card ── */
.project-card {
  background: var(--white);
  border-radius: var(--radius-card);
  overflow: hidden;
  box-shadow: var(--shadow-sm);
  border: 1px solid rgba(138, 8, 8, 0.07);
  display: flex;
  flex-direction: column;
  transition:
    transform  0.4s cubic-bezier(0.23, 1, 0.32, 1),
    box-shadow 0.4s cubic-bezier(0.23, 1, 0.32, 1);
  animation: fadeUp 0.55s both;
  animation-delay: var(--delay, 0ms);
}
 
.project-card:hover {
  transform: translateY(-10px);
  box-shadow: var(--shadow-lg);
}
 
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(28px); }
  to   { opacity: 1; transform: translateY(0); }
}
 
/* ── Image ── */
/* Imagem flutuante com padding lateral — dá respiro visual e reforça o arredondamento */
.card-image-wrap {
  position: relative;
  aspect-ratio: 16 / 9;
  overflow: hidden;
  background: #e8d8be;
  border-radius: var(--radius-img);
  margin: 10px 10px 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
 
.card-image {
  width: 100%;
  height: 100%;
  border-radius: var(--radius-img);
  object-fit: cover;
  object-position: center center;
  display: block;
  transition: transform 0.65s cubic-bezier(0.23, 1, 0.32, 1);
}
 
.project-card:hover .card-image {
  transform: scale(1.07);
}
 
/* Overlay com botão Visualizar */
.card-image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    160deg,
    rgba(26, 16, 8, 0) 30%,
    rgba(26, 16, 8, 0.58) 100%
  );
  display: flex;
  align-items: flex-end;
  justify-content: flex-start;
  padding: 18px;
  opacity: 0;
  transition: opacity 0.35s ease;
}
 
.project-card:hover .card-image-overlay {
  opacity: 1;
}
 
.overlay-btn {
  color: white;
  display: inline-flex;
  align-items: center;
  gap: 7px;
  background: var(--white);
  color: var(--red);
  font-family: 'DM Sans', sans-serif;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-decoration: none;
  text-transform: uppercase;
  padding: 7px 16px;
  border-radius: 100px;
  transform: translateY(8px);
  transition:
    transform   0.35s cubic-bezier(0.23, 1, 0.32, 1),
    background  0.2s ease,
    color       0.2s ease,
    box-shadow  0.2s ease;
  box-shadow: 0 4px 16px rgba(138, 8, 8, 0.20);
}
 
.project-card:hover .overlay-btn {
  transform: translateY(0);
}
 
.overlay-btn:hover {
  color: #ffffff;
  background: var(--red);
  color: var(--white);
  box-shadow: 0 6px 20px rgba(138, 8, 8, 0.38);
}
 
/* ── Card Body ── */
.card-body {
  padding: clamp(16px, 2.2vw, 24px) clamp(18px, 2.5vw, 26px) clamp(18px, 2.5vw, 22px);
  display: flex;
  flex-direction: column;
  flex: 1;
  gap: 10px;
}
 
/* Tags */
.card-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}
 
.tag {
  font-size: 0.63rem;
  font-weight: 600;
  letter-spacing: 0.09em;
  text-transform: uppercase;
  color: var(--red);
  background: var(--red-light);
  border: 1px solid var(--border);
  padding: 3px 11px;
  border-radius: 100px;
  transition: background 0.2s, color 0.2s;
}
 
.tag:hover {
  background: var(--red);
  color: var(--white);
  cursor: default;
}
 
/* Title */
.card-title {
  font-family: 'Playfair Display', Georgia, serif;
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--ink);
  margin: 0;
  line-height: 1.25;
  letter-spacing: -0.015em;
}
 
/* Description */
.card-description {
  font-size: 0.85rem;
  color: var(--ink-soft);
  line-height: 1.7;
  margin: 0;
  flex: 1;
  font-weight: 300;
}
 
/* ── Card Footer ── */
.card-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 16px;
  margin-top: 4px;
  border-top: 1px solid var(--border);
}
 
/* Botão Visualizar — ghost com borda azul, texto azul (maior contraste) */
.btn-visualizar {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  background: transparent;
  color: #1a6fd4;
  text-decoration: none;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.76rem;
  font-weight: 700;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  padding: 7px 18px;
  border-radius: 100px;
  border: 1.5px solid #1a6fd4;
  transition:
    background  0.25s ease,
    color       0.25s ease,
    box-shadow  0.25s ease,
    transform   0.2s ease;
}
 
.btn-visualizar:hover {
  background: #1a6fd4;
  color: var(--white);
  box-shadow: 0 4px 18px rgba(26, 111, 212, 0.30);
  transform: translateY(-1px);
}
 
/* Número decorativo */
.card-index {
  font-family: 'Playfair Display', serif;
  font-size: 1.85rem;
  font-weight: 700;
  color: rgba(138, 8, 8, 0.09);
  line-height: 1;
  user-select: none;
  letter-spacing: -0.04em;
}
 
/* ── Responsive ── */
@media (max-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
 
@media (max-width: 640px) {
  .portfolio-page {
    padding: 48px 18px 64px;
  }
 
  .projects-grid {
    grid-template-columns: 1fr;
    gap: 24px;
  }
 
  .section-title {
    font-size: 2.2rem;
  }
 
  .card-image-wrap {
    margin: 8px 8px 0;
  }
 
  .card-body {
    padding: 18px;
  }
 
  .card-index {
    font-size: 1.4rem;
  }
}
</style>