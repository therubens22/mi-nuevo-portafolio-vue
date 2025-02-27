<template>
    <section id="contact" class="contact">
      
        <h2>Contacto</h2>
        <form @submit.prevent="enviarFormulario">
          <label for="nombre">Nombre:</label>
          <input type="text" id="nombre" v-model="form.nombre" required />
  
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="form.email" required />
  
          <label for="mensaje">Mensaje:</label>
          <textarea id="mensaje" v-model="form.mensaje" required></textarea>
  
          <button type="submit">Enviar</button>
  
          <p v-if="mensajeEnviado" class="mensaje-exito">
            ¡Mensaje enviado con éxito!
          </p>
        </form>
   
    </section>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
  const form = ref({
    nombre: "",
    email: "",
    mensaje: "",
  });
  
  const mensajeEnviado = ref(false);
  const endpointFormspree = "https://formspree.io/f/tu-endpoint"; // Reemplaza con tu endpoint real
  
  const enviarFormulario = async () => {
    try {
      const response = await fetch(endpointFormspree, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(form.value),
      });
  
      if (response.ok) {
        mensajeEnviado.value = true;
        form.value = { nombre: "", email: "", mensaje: "" }; // Reset form
      } else {
        console.error("Error al enviar el formulario");
      }
    } catch (error) {
      console.error("Error en la solicitud:", error);
    }
  };
  </script>
  
  <style scoped>

.contact {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: white;
    padding: 3rem 2rem;
    max-width: 1000px; /* Asegura que el contenedor tenga el mismo ancho que el de arriba */
    margin: 0 auto; /* Centra horizontalmente */
    width: 100%;
}

h2 {
    font-size: 50px;
    margin-bottom: 20px;
}

form {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%; /* 🔹 Hace el formulario más ancho */
    max-width: 900px; /* 🔹 Ajusta el ancho del formulario */
    padding: 2rem;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 10px;
}

label {
    text-align: left;
    width: 100%;
    margin-top: 10px;
}

input,
textarea {
    width: 100%;
    padding: 8px;
    margin-top: 5px;
    border-radius: 5px;
    border: none;
    font-size: 14px;
}

button {
    margin: 15px auto;
    padding: 10px 20px;
    background: var(--secundario);
    color: white;
    border: 3px solid var(--secundario); /* 🔹 Agrega el borde desde el inicio */
    border-radius: 15px;
    cursor: pointer;
    font-size: 18px;
    width: fit-content;
    transition: background 0.3s ease-in-out, color 0.3s ease-in-out;
}

button:hover {
    background: transparent;
    color: var(--secundario);
}


  </style>
  