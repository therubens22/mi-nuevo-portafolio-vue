<template>
  <h2>Porfolio</h2>
  <div class="portfolio-container">
    <div class="carousel">
      <div 
        class="carousel-track"
        :style="trackStyle"
        @transitionend="handleTransitionEnd"
      >
        <div 
          v-for="(project, index) in projects" 
          :key="index" 
          class="carousel-item"
        >
          <img :src="project.image" :alt="project.title" />
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
          <a :href="project.link" target="_blank">Ver más</a>
        </div>
      </div>
    </div>
    <button @click="prevSlide">&#10094;</button>
    <button @click="nextSlide">&#10095;</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 1, // Comenzamos en la primera imagen real
      transitioning: false,
      projects: [
  { 
    image: new URL('@/assets/img/porfolio/4.png', import.meta.url).href, 
    title: 'Juego de Memoria', 
    description: 'Un divertido juego interactivo para entrenar la memoria.', 
    link: '#' 
  }, // Imagen duplicada al inicio

  { 
    image: new URL('@/assets/img/porfolio/1.png', import.meta.url).href, 
    title: 'AECVA', 
    description: 'Asociación de Etología Clínica Veterinaria Argentina.', 
    link: 'https://veterinaria-kappa.vercel.app/' 
  },

  { 
    image: new URL('@/assets/img/porfolio/2.png', import.meta.url).href, 
    title: 'LoginLoom', 
    description: 'Sistema de autenticación seguro y fácil de usar.', 
    link: 'https://login-pi-olive.vercel.app/' 
  },

  { 
    image: new URL('@/assets/img/porfolio/3.png', import.meta.url).href, 
    title: 'Landing Page', 
    description: 'Diseño atractivo y responsivo para promoción de servicios.', 
    link: 'https://landing-pages-sage-rho.vercel.app/' 
  },

  { 
    image: new URL('@/assets/img/porfolio/4.png', import.meta.url).href, 
    title: 'Juego de Memoria', 
    description: 'Un divertido juego interactivo para entrenar la memoria.', 
    link: 'https://juego-menoria.vercel.app/' 
  }, 

  { 
    image: new URL('@/assets/img/porfolio/1.png', import.meta.url).href, 
    title: 'AECVA', 
    description: 'Asociación de Etología Clínica Veterinaria Argentina.', 
    link: 'https://veterinaria-kappa.vercel.app/' 
  } // Imagen duplicada al final
]

    };
  },
  computed: {
    trackStyle() {
      return {
        transform: `translateX(-${this.currentIndex * 100}%)`,
        transition: this.transitioning ? "transform 0.5s ease-in-out" : "none"
      };
    }
  },
  methods: {
    nextSlide() {
      if (this.transitioning) return;
      this.transitioning = true;
      this.currentIndex++;

      // Si llegamos a la imagen duplicada, corregimos el índice al terminar la animación
      setTimeout(() => {
        if (this.currentIndex >= this.projects.length - 1) {
          this.transitioning = false;
          this.currentIndex = 1;
          this.resetTransition();
        }
      }, 500);
    },
    prevSlide() {
      if (this.transitioning) return;
      this.transitioning = true;
      this.currentIndex--;

      // Si llegamos a la imagen duplicada al inicio, corregimos el índice al terminar la animación
      setTimeout(() => {
        if (this.currentIndex <= 0) {
          this.transitioning = false;
          this.currentIndex = this.projects.length - 2;
          this.resetTransition();
        }
      }, 500);
    },
    handleTransitionEnd() {
      if (this.currentIndex === this.projects.length - 1) {
        this.currentIndex = 1;
        this.resetTransition();
      } else if (this.currentIndex === 0) {
        this.currentIndex = this.projects.length - 2;
        this.resetTransition();
      }
      this.transitioning = false;
    },
    resetTransition() {
      requestAnimationFrame(() => {
        requestAnimationFrame(() => {
          this.transitioning = false;
        });
      });
    }
  }
};
</script>

<style scoped>

h2 {
  color: black;
    font-size: 50px;
    margin-bottom: 20px;
}

.portfolio-container {
  position: relative;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.carousel {
  display: flex;
  align-items: center;
  position: relative;
  width: 80%;
  overflow: hidden;
}

.carousel-track {
  display: flex;
  align-items: center; /* Centra los elementos verticalmente */
}
.carousel-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  flex: 1 0 100%;
  min-width: 100%;
  box-sizing: border-box;
  text-align: center;
  flex-shrink: 0;
}

.carousel-item img {
  width: 100%; /* Que ocupe todo el ancho */
  max-width: 400px; /* Ajusta este valor si es necesario */
  height: auto;
  object-fit: contain;
  display: block;
}


button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: var(--secundario);
  border: 3px solid var(--secundario); /* 🔹 Agrega el borde desde el inicio */
  color: white;
  border-radius: 10px;
  cursor: pointer;
  padding: 10px;
  transition: background 0.3s ease-in-out, color 0.3s ease-in-out;
  z-index: 10;
}

button:hover {
    background: transparent;
    
    color: var(--secundario);
}

button:first-of-type {
  left: 15px;
}

button:last-of-type {
  right: 15px;
}

h3 {
  color: var(--secundario);
  font-size: 30px;
}
 p{
  color: var(--oscuro);
 }


a {
  display: inline-block;
  text-decoration: none;
  margin: 15px auto;
  padding: 10px 20px;
  background: var(--secundario);
  color: white;
  border: 3px solid var(--secundario);
  border-radius: 15px;
  cursor: pointer;
  font-size: 18px;
  width: fit-content;
  transition: background 0.3s ease-in-out, color 0.3s ease-in-out;
}

a:hover {
  background: transparent;
  color: var(--secundario);
}


@media (max-width: 1024px) {
  .carousel {
    width: 100%;
  }
  
  h2 {
    font-size: 40px;
  }
  
  h3 {
    font-size: 25px;
  }

  p {
    font-size: 16px;
  }
}

@media (max-width: 768px) {
  .carousel {
    width: 95%;
  }

  .carousel-item img {
    max-width: 90%;
  }

  button {
    padding: 8px;
    font-size: 16px;
  }

  h2 {
    font-size: 30px;
  }

  h3 {
    font-size: 20px;
  }

  p {
    font-size: 14px;
  }

  a {
    font-size: 16px;
    padding: 8px 15px;
  }
}

@media (max-width: 480px) {
  .carousel {
    width: 100%;
  }

  h2 {
    font-size: 25px;
  }

  h3 {
    font-size: 18px;
  }

  p {
    font-size: 12px;
  }

  button {
    padding: 5px;
    font-size: 14px;
  }

  a {
    font-size: 14px;
    padding: 6px 12px;
  }
}


</style>
