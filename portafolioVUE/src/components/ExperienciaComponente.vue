<script setup>
import { ref, inject } from "vue";

// Importar íconos
import icono2 from "/src/assets/python-svgrepo-com.svg";
import icono3 from "/src/assets/mountain-part-2-svgrepo-com.svg";
import icono4 from "/src/assets/tool.svg";

// Recibir tema global (light/dark)
const theme = inject("theme", ref("light"));

// Experiencias
const experiencias = ref([
  {
    id: 1,
    src: icono2,
    parrafo:
      "Agenda telefónica (Python): Aplicación CRUD con menú para alta, baja, modificación y consulta de contactos. (Tecnologías: Python, OOP, estructuras de datos, control de flujo)",
  },
  {
    id: 2,
    src: icono2,
    parrafo:
      "Estación meteorológica (IoT): Proyecto en Python + electrónica ESP32 para capturar y enviar datos meteorológicos. (Tecnologías: Python, sensores IoT, comunicación serial, electrónica básica)",
  },
  {
    id: 3,
    src: icono3,
    parrafo:
      "Página web personal (HTML/CSS/JavaScript): Portfolio online para mostrar proyectos. (Tecnologías: HTML5, CSS3, JavaScript, diseño responsive)",
  },
  {
    id: 4,
    src: icono4,
    parrafo:
      "Sistema de stock y ventas (Java): CRUD de productos con simulación de facturación en consola. (Tecnologías: Java, POO, SQL, manejo de excepciones, estructuras de datos)",
  },
]);
</script>

<template>
  <div class="card" :class="theme">
    <h3 class="titulo">Estudiante de Programación</h3>
    <p class="fecha">Marzo 2025 - Actualidad</p>

    <ul class="listado">
      <li class="item" v-for="experiencia in experiencias" :key="experiencia.id">
        <img
          class="imagen-svg"
          :src="experiencia.src"
          :alt="experiencia.parrafo"
          width="45"
        />
        <p>{{ experiencia.parrafo }}</p>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  padding: 2rem;
  background-color: var(--color-background-soft);
  border-radius: 15px;
  border: 1px solid var(--color-border);
  transition: background-color 0.4s, color 0.4s;
}

.titulo {
  font-size: 2rem;
  color: var(--color-heading);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-bottom: 0.5rem;
  text-shadow: 0 0 10px rgba(0, 0, 0, 0.15);
}

.fecha {
  font-size: 1.1rem;
  color: var(--color-text);
  margin-bottom: 1.5rem;
  font-style: italic;
  letter-spacing: 1px;
  opacity: 0.9;
}

.listado {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.item {
  align-items: center;
  display: flex;
  padding: 1rem;
  gap: 1.5rem;
  background-color: var(--color-background-mute);
  border-radius: 12px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.item:hover {
  transform: translateY(-4px);
}

.item p {
  color: var(--color-text);
}

.imagen-svg {
  width: 45px;
  height: 45px;
}
</style>