<template>
    <section class="contenedor-principal">
      <div class="contenido">
        <!-- Sección Sobre Mí -->
        <SobreMi />
  
        <!-- Sección Habilidades -->
        <Skills />
  
        <!-- Sección Portafolio -->
        <Portfolio />
      </div>
    </section>
  </template>
  
  <script>
  import SobreMi from '@/components/SobreMi.vue';
  import Skills from '@/components/Skills.vue';
  import Portfolio from '@/components/Portfolio.vue';
  
  export default {
    components: {
      SobreMi,
      Skills,
      Portfolio
    }
  };
  </script>
  
  <style scoped>
  /* 🔹 Contenedor blanco que ocupa TODA la pantalla */
  .contenedor-principal {
    background: white; /* Fondo blanco */
    width: 100vw; /* Ancho del 100% de la pantalla */
    height: 100vh; /* Alto del 100% de la pantalla */
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  /* 🔹 Contenido centrado dentro del contenedor */
  .contenido {
    max-width: 900px; /* Ancho máximo */
    width: 100%;
    padding: 2rem;
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }
  </style>
  