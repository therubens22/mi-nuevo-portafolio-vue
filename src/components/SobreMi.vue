<template>
  <section id="sobre-mi" class="sobre-mi">
    <div class="container">
      <h2>Mi Nombre es: Orlando</h2>
      <p>
        Soy un apasionado por la programación. La disciplina, dedicación y compromiso son tres factores que me definen.
        Me gusta dar siempre lo mejor de mí en todo, por más simple o complejo que pueda ser el desafío.
      </p>
      
      <!-- Enlaces sociales -->
      <div class="social-links">
        <a href="https://github.com/therubens22" target="_blank">
          <img src="@/assets/img/iconos/git.svg" alt="git" class="icono" />
        </a>
        <a href="https://www.linkedin.com/in/tu-perfil" target="_blank">
          <img src="@/assets/img/iconos/linkedin.svg" alt="linkedin" class="icono" />
        </a>
        <a href="mailto:tuemail@example.com">
          <img src="@/assets/img/iconos/gmail.svg" alt="gmail" class="icono" />
        </a>
      </div>

      <!-- Botón de descarga -->
      <a href="/Cv-OrlandoEscalante.pdf" download="Cv-OrlandoEscalante.pdf">
        <button type="button">Descargar CV</button>
      </a>
    </div>
  </section>
</template>

<style scoped>
/* 🎨 Sección principal */
.sobre-mi {
  width: 100%;
  display: flex;
  justify-content: center;
  padding: 4rem 2rem;
}

/* Contenedor con fondo blanco */
.container {
  width: 90%;
  max-width: 1000px;
  background: white;
  color: black;
  padding: 3rem;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.5);
  text-align: center;
}

/* Título */
h2 {
  font-size: 3rem;
  margin-bottom: 1rem;
}

/* Texto */
p {
  font-size: 1.4rem;
  line-height: 1.6;
}

/* Íconos sociales */
.social-links {
  margin: 2rem 0;
  display: flex;
  justify-content: center;
  gap: 1.5rem;
}

.icono {
  width: 50px;
  height: 50px;
  transition: transform 0.3s ease-in-out;
}

.icono:hover {
  transform: scale(1.1);
}

/* Botón */
button {
  padding: 10px 20px;
  background: var(--secundario);
  color: white;
  border: 3px solid var(--secundario);
  border-radius: 15px;
  cursor: pointer;
  font-size: 18px;
  transition: background 0.3s ease-in-out, color 0.3s ease-in-out;
}

button:hover {
  background: transparent;
  color: var(--secundario);
}

/* 📱 Responsividad */
@media (max-width: 768px) {
  .container {
    padding: 2rem;
  }

  h2 {
    font-size: 2.5rem;
  }

  p {
    font-size: 1.2rem;
  }

  .icono {
    width: 40px;
    height: 40px;
  }
}

@media (max-width: 480px) {
  h2 {
    font-size: 2rem;
  }

  p {
    font-size: 1.1rem;
  }

  .icono {
    width: 35px;
    height: 35px;
  }
}
</style>
