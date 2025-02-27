<template>
  <header class="header">
    <nav class="nav">
      <div class="logo-container">
        <img src="@/assets/img/logopropio.png" alt="Logo" class="logo" />
      </div>
      
      <!-- Botón de menú a la derecha -->
      <button class="menu-btn" @click="menuAbierto = !menuAbierto">
        {{ menuAbierto ? '✖' : '☰' }}
      </button>

      <!-- Menú de navegación -->
      <ul :class="['nav-links', { 'nav-open': menuAbierto }]">
        <li><a href="#sobre-mi" @click="cerrarMenu">Sobre Mí</a></li>
        <li><a href="#habilidades" @click="cerrarMenu">Habilidades</a></li>
        <li><a href="#portfolio" @click="cerrarMenu">Portafolio</a></li>
        <li><a href="#contacto" @click="cerrarMenu">Contacto</a></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      menuAbierto: false
    };
  },
  methods: {
    cerrarMenu() {
      this.menuAbierto = false;
    },
    manejarClicFuera(event) {
      const menu = this.$el.querySelector(".nav-links");
      const boton = this.$el.querySelector(".menu-btn");
      if (
        this.menuAbierto &&
        !menu.contains(event.target) &&
        !boton.contains(event.target)
      ) {
        this.cerrarMenu();
      }
    }
  },
  mounted() {
    window.addEventListener("click", this.manejarClicFuera);
  },
  beforeUnmount() {
    window.removeEventListener("click", this.manejarClicFuera);
  }
};
</script>


<style scoped>

/* Estilos generales */
.header {
  background: var(--secundario);
  color: white;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  text-align: center;
  position: relative;
  z-index: 100;
}

/* Logo siempre visible */
.logo-container {
  display: flex;
  align-items: center;

}

.logo {
  height: auto;
  width: auto;
  margin-top: 50px;
}

/* 🔹 MENÚ EN MÓVIL (Oculto por defecto) */
.nav-links {
  list-style: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: fixed;
  top: 0;
  right: 0;
  width: 100%;
  height: 40vh;
  background: var(--secundario);
  transform: translateX(100%); /* 🔥 Ocultamos completamente */
  transition: transform 0.3s ease-in-out;
  z-index: 50;
  box-shadow: -5px 0 10px rgba(0, 0, 0, 0.2);
  padding: 0; /* Ajusta el padding a 0 para evitar el espacio extra */
  justify-content: center; /* Centra los elementos verticalmente */
}

/* Menú abierto */
.nav-links.nav-open {
  transform: translateX(0); /* 🔥 Se muestra correctamente */
}

/* Links del menú */
.nav-links li {
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
  width: 100%; /* Ocupa todo el ancho para asegurar que los enlaces se alineen */
  text-align: center; /* Asegura que los enlaces se centren */
}

.nav-open li {
  opacity: 1;
  transition-delay: 0.2s;
}

.nav-links a {
  color: white;
  text-decoration: none;
  font-size: 22px;
  padding: 25px 0;
  display: block;
}

.nav-links a:hover{
  color: black;
}

/* 🔹 Botón hamburguesa */
.menu-btn {
  background: none;
  border: none;
  color: white;
  font-size: 30px;
  cursor: pointer;
  z-index: 100;
  position: absolute;
  right: 20px;
  top: 15px;
}

/* 🔹 AJUSTES PARA ESCRITORIO */
@media (min-width: 769px) {
  .menu-btn {
    display: none; /* 🔥 Oculta el botón hamburguesa */
  }

  .nav-links {
    position: absolute; /* 🔥 Permite que se vea en PC */
    transform: none; /* 🔥 Anula el efecto de ocultar */
    height: auto;
    flex-direction: row;
    background: none;
    display: flex;
    width: auto;
    box-shadow: none;
  }

  .nav-links li {
    opacity: 1; /* 🔥 Siempre visibles */
    margin: 0 15px;
  }
}


</style>
