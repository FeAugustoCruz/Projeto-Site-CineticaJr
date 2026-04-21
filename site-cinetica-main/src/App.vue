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
      class="whatsapp-button"
    >
      💬
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

/* Botão WhatsApp */
.whatsapp-button {
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 60px;
  height: 60px;
  background-color: #25D366;
  color: white;
  font-size: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  text-decoration: none;
  box-shadow: 0 4px 12px rgba(0,0,0,0.3);
  transition: transform 0.3s ease;
  z-index: 1000;

  animation: pulse 1.5s infinite;
}

.whatsapp-button:hover {
  transform: scale(1.1);
}

/* Animação estilo sites modernos */
@keyframes pulse {
  0% {
    box-shadow: 0 0 0 0 rgba(37, 211, 102, 0.7);
  }
  70% {
    box-shadow: 0 0 0 15px rgba(37, 211, 102, 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(37, 211, 102, 0);
  }
}
</style>
