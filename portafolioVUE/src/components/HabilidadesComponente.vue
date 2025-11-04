<script setup>
// Se importa ref de vue para poder usarlo
import { ref } from 'vue';

// Se crea un array de objetos con las habilidades
// Este es un array de objetos con habilidades que se pueden modificar o agregar
const habilidades = ref([
  {
    // Se crea un objeto con id, nombre y habilidades
    id: 1,
    nombre: 'Lenguajes de Programación',
    habilidades: [
      // Se crea un objeto con id, nombre, nivel e icono
      { id: 1, nombre: 'JavaScript', icono: '/src/components/icons/js.svg' },
      { id: 2, nombre: 'Python', icono: '/src/components/icons/python.svg' },
      { id: 3, nombre: 'HTML/CSS', icono: '/src/components/icons/html-css.svg' },
      { id: 4, nombre: 'Java', icono: '/src/components/icons/java.svg' },
      { id: 5, nombre: 'SQL', icono: '/src/components/icons/sql.svg' }
    ]
  },
  {
    id: 2,
    nombre: 'Frameworks y Librerías',
    habilidades: [
      { id: 1, nombre: 'React.js', icono: '/src/components/icons/react.svg' },
      { id: 2, nombre: 'Vue.js', icono: '/src/components/icons/vue.svg' },
      { id: 3, nombre: 'Node.js', icono: '/src/components/icons/node.svg' },
      { id: 4, nombre: 'Django', icono: '/src/components/icons/django.svg' },
      { id: 5, nombre: 'Bootstrap', icono: '/src/components/icons/bootstrap.svg' }
    ]
  },
  {
  id: 3, nombre: 'Herramientas y Software', habilidades: [
    { id: 1, nombre: 'Git', icono: '/src/components/icons/git.svg' },
    { id: 2, nombre: 'Docker',  icono: '/src/components/icons/docker.svg' },
    { id: 3, nombre: 'Cypress', icono: '/src/components/icons/cypress.svg' },
    { id: 4, nombre: 'Figma', icono: '/src/components/icons/figma.svg' },
    { id: 5, nombre: 'Visual Studio Code', icono: '/src/components/icons/visual.svg' }
  ]
},
{
  id: 4, nombre: 'Bases de Datos', habilidades: [
    { id: 1, nombre: 'MongoDB', icono: '/src/components/icons/mongo.svg' },
    { id: 2, nombre: 'MySQL', icono: '/src/components/icons/mysql.svg' },
    { id: 3, nombre: 'PostgreSQL', icono: '/src/components/icons/postgres.svg' }
  ]
},
{
  id: 5, nombre: 'Idiomas', habilidades: [
    { id: 1, nombre: 'Español', nivel: 'Nativo', icono: '/src/components/icons/arg.svg' },
    { id: 2, nombre: 'Inglés', nivel: 'Avanzado ', icono: '/src/components/icons/eeuu.svg' }
  ]
}
]);
</script>
<template>
  <!--Este componente se utiliza de esta forma:-->
  <div class="skills-contenedor">
    <!--Se recorre el array habilidades con v-for y se asigna la key habilidad.id-->
    <div v-for="habilidad in habilidades" :key="habilidad.id" class="skills-categoria">
      <!--Se muestra el nombre de la habilidad-->
      <h3>{{ habilidad.nombre }}</h3>
      <ul class="skills">
        <!--Se recorre el array habilidades con v-for y se asigna la key habilidad.id-->
        <li v-for="habilidad in habilidad.habilidades" :key="habilidad.id" class="skill">
          <!--Se muestra el ícono de la habilidad y el nombre de la habilidad con su nivel-->
          <img :src="habilidad.icono" :alt="habilidad.nombre">
          <span>{{ habilidad.nombre }}: {{ habilidad.nivel }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>
<style scoped>
.skills-contenedor {
  position: relative;
  padding: 2rem;
  border-radius: 12px;
  overflow: hidden;

  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
  align-items: start;

  background: var(--color-background-soft);
  transition: background-color 0.5s ease, color 0.5s ease;
  border: 1px solid var(--color-border);
}

.skills-categoria {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
}

.skills-categoria h3 {
  margin: 0;
  font-size: 1.25rem;
  font-weight: 800;
  color: var(--color-heading);
  transition: color 0.3s;
}

.skills {
  display: grid;
  grid-template-columns: 1fr;
  gap: 12px;
  list-style: none;
  padding: 0;
  margin: 0;
}

.skill {
  display: flex;
  align-items: center;
  gap: 12px;
  background: var(--color-background-mute);
  padding: 12px;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.08);
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.skill:hover {
  transform: translateY(-4px);
}

.skill img {
  width: 36px;
  height: 36px;
  flex-shrink: 0;
}

.skill span {
  font-size: 1rem;
  color: var(--color-text);
}

@media (max-width: 768px) {
  .skills-contenedor {
    grid-template-columns: 1fr;
    padding: 1rem;
  }
}
</style>