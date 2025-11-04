<script setup>
import perfil from '@/assets/perfil.jpg';
</script>

<template>
  <section class="datos-personales">
    <img :src="perfil" alt="Foto de perfil" class="perfil" />

    <div class="info">
      <h1>Federico Martínez Carballada</h1>
      <h2>Técnico Universitario en Programación</h2>
      <p>
        Soy estudiante de la Tecnicatura Universitaria en Programación en la UTN, apasionado por la tecnología, el desarrollo web y la resolución creativa de problemas. Busco seguir creciendo profesionalmente mientras aplico buenas prácticas de código y diseño.
      </p>

      <div class="links">
        <a href="https://www.linkedin.com/in/femarcarb" target="_blank">LinkedIn</a>
        <a href="https://github.com/fedestroy" target="_blank">GitHub</a>
        <a>Descargar CV</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.datos-personales {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 2rem;
  padding: 2rem;
  background: var(--color-bg, #f8f9fa);
  color: var(--color-text, #222);
  text-align: center;
}

.perfil {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
}

.info {
  max-width: 600px;
}

h1 {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

h2 {
  font-size: 1.2rem;
  color: #666;
  margin-bottom: 1rem;
}

p {
  line-height: 1.5;
  margin-bottom: 1.5rem;
}

.links {
  display: flex;
  justify-content: center;
  gap: 1.2rem;
  flex-wrap: wrap;
}

.links a {
  background: linear-gradient(90deg, #007bff, #00c3ff);
  color: white;
  padding: 0.6rem 1.2rem;
  border-radius: 20px;
  text-decoration: none;
  font-weight: bold;
  transition: all 0.3s ease;
}

.links a:hover {
  background: linear-gradient(90deg, #0056b3, #009ecf);
  transform: translateY(-3px);
}
</style>