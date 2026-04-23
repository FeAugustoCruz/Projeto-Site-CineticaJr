<template>
  <div>
    <AppHeader />
    
    <main class="main-content">
      <router-view/>
    </main>
 
    <!-- Botão WhatsApp -->
    <a 
      href="https://wa.me/5599999999999" 
      target="_blank" 
      rel="noopener noreferrer"
      class="whatsapp-button"
      aria-label="Fale conosco pelo WhatsApp"
    >
      <img src="./assets/img/whatsapp.png" alt="WhatsApp" class="whatsapp-icon" />
    </a>
  </div>
</template>
 
<script>
import AppHeader from './components/header.vue';
 
export default {
  name: 'App',
  components: {
    AppHeader
  }
}
</script>
 
<style>
html, body {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
  overflow: auto;
}
 
.main-content {
  padding-top: 100px;
}
 
/* ── Botão WhatsApp ── */
.whatsapp-button {
  position: fixed;
  bottom: 24px;
  right: 24px;
  width: 56px;
  height: 56px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
  transition: transform 0.25s cubic-bezier(0.4, 0, 0.2, 1),
              box-shadow 0.25s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 2000;
  overflow: hidden;
}
 
.whatsapp-button:hover {
  transform: scale(1.1) translateY(-2px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.25);
}
 
.whatsapp-button:active {
  transform: scale(0.96);
}
 
.whatsapp-icon {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
  border-radius: 50%;
}
 
/* Responsivo — menor em telas pequenas */
@media (max-width: 480px) {
  .whatsapp-button {
    width: 48px;
    height: 48px;
    bottom: 16px;
    right: 16px;
  }
}
</style>
 