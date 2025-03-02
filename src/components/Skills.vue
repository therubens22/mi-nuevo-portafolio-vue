<template>
  <section id="habilidades" class="habilidades">
    <div class="container">
      <h2>Habilidades</h2>

      <div class="skills-list">
        <div class="skill" v-for="(skill, index) in skills" :key="index">
          <p>{{ skill.name }}</p>
          <div class="progress-bar">
            <div class="progress" :style="{ width: skill.level + '%' }"></div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
const skills = [
  { name: "HTML", level: 90 },
  { name: "CSS", level: 90 },
  { name: "JavaScript", level: 75 },
  { name: "Vue", level: 65 },
  { name: "Python", level: 50 },
  { name: "Tailwind", level: 70 },
];
</script>

<style scoped>
h2 {
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.habilidades {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 4rem 2rem;
  width: 100%;
}

.container {
  width: 100%;
  max-width: 800px;
  background: white;
  color: black;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
}

/* Contenedor de habilidades */
.skills-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

/* Estilos para las habilidades */
.skill p {
  margin: 0 0 8px;
  font-size: 1.2rem;
  font-weight: bold;
  text-align: left;
}

/* Estilos para las barras de progreso */
.progress-bar {
  width: 100%;
  height: 15px; /* Ajustado para mejor visibilidad en móviles */
  background: #ddd;
  border-radius: 10px;
  overflow: hidden;
}

.progress {
  height: 100%;
  background: var(--secundario, #00bcd4);
  transition: width 0.5s ease-in-out;
}

/* Responsividad */
@media (max-width: 768px) {
  .container {
    padding: 1.5rem;
  }

  h2 {
    font-size: 2rem;
  }

  .skill p {
    font-size: 1rem;
  }

  .progress-bar {
    height: 12px;
  }
}
</style>
