<template>
  <section id="inicio" class="hero">
    <div class="overlay"></div> <!-- Capa oscura -->
    <div class="container">
      <h2>Developer</h2>
      <p>Front End</p>
    </div>
  </section>
</template>

<style scoped>
/* Sección Hero */
.hero {
  background-image: url("@/assets/img/banner.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  color: white;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh; /* Ocupa toda la pantalla */
  padding: 5rem 2rem;
}

/* Capa oscura */
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 1;
}

/* Asegurar que el contenido esté por encima de la capa oscura */
.container {
  position: relative;
  z-index: 2;
}

/* Texto principal */
h2 {
  font-size: 6rem;
  font-family: 'Oswald', sans-serif;
  font-weight: 700;
  transition: color 0.5s ease-in-out, transform 0.5s ease-in-out;
}

p {
  font-size: 3rem;
  font-family: 'Oswald', sans-serif;
  font-weight: 400;
  transition: color 0.5s ease-in-out, transform 0.5s ease-in-out;
}

/* Hover solo en pantallas grandes */
@media (min-width: 768px) {
  h2:hover, p:hover {
    color: var(--secundario);
    transform: scale(1.1);
  }
}

/* 📱 Ajustes Responsive */
@media (max-width: 1024px) {
  h2 {
    font-size: 4rem;
  }
  p {
    font-size: 2rem;
  }
}

@media (max-width: 768px) {
  .hero {
    height: 80vh;
    padding: 3rem 1rem;
  }
  h2 {
    font-size: 3rem;
  }
  p {
    font-size: 1.8rem;
  }
}

@media (max-width: 480px) {
  h2 {
    font-size: 2.5rem;
  }
  p {
    font-size: 1.5rem;
  }
}
</style>
