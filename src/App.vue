<template>
  <div id="app">
    <Header /> <!-- 🔹 Header ocupa todo el ancho -->
    <Hero /> <!-- 🔹 Hero ocupa todo el ancho -->
    
    <main class="contenedor-blanco">
      <SobreMi />
      <Skills />
      <Portfolio />
    </main>

    <ContactForm /> <!-- 🔹 Fuera del contenedor blanco -->
    <Footer />
  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import Hero from '@/components/Hero.vue';
import SobreMi from '@/components/SobreMi.vue';
import Skills from '@/components/Skills.vue';
import Portfolio from '@/components/Portfolio.vue';
import ContactForm from '@/components/ContactForm.vue';
import Footer from '@/components/Footer.vue';

export default {
  components: {
    Header,
    Hero,
    SobreMi,
    Skills,
    Portfolio,
    ContactForm,
    Footer
  }
};
</script>

<style>
/* 🔹 Fondo oscuro para toda la pantalla */
body {
  background-color: #222;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* 🔹 Contenedor Blanco */
.contenedor-blanco {
  background: white;
  width: 90%;
  max-width: 900px;
  padding: 2rem;
  margin: 2rem auto;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* 🔹 ContactForm y Footer ocupan todo el ancho */
.contacto,
.footer {
  width: 100%;
}
</style>
