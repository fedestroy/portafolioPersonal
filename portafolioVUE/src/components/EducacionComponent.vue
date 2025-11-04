<script setup>
import { ref, inject, computed } from "vue";

// Recibimos el tema global desde App.vue (isDark = ref(boolean))
const isDark = inject("theme", ref(false));

// Colores alternados por ítem
const fechaColor = ref([
  { color: "#69C5FF", fg: "#ffffff", border: "#69C5FF" },
  { color: "#FBCA3E", fg: "#1b1b1b", border: "#FBCA3E" },
  { color: "#69C5FF", fg: "#ffffff", border: "#69C5FF" },
  { color: "#FBCA3E", fg: "#1b1b1b", border: "#FBCA3E" },
  { color: "#69C5FF", fg: "#ffffff", border: "#69C5FF" },
]);

// Contenido educativo
const educacion = ref([
  {
    fecha: "2025-2026",
    title: "Técnicatura Universitaria en Programación - UTN",
    descripcion:
      "Con orientación al desarrollo fullstack con fuerte base en backend y conocimientos en Python, Java, JavaScript, HTML, CSS, MySQL, etc.",
    enlace: "https://www.frsr.utn.edu.ar/programacion/",
  },
  {
    fecha: "2025",
    title: "Curso Profesional de Ciberseguridad de Google - Google Career",
    descripcion:
      "Profesional de ciberseguridad con experiencia en la protección de infraestructuras críticas, incluyendo el diseño de estrategias de seguridad, gestión de vulnerabilidades y respuesta a incidentes.",
    enlace:
      "https://www.coursera.org/professional-certificates/google-cybersecurity/",
  },
  {
    fecha: "2025",
    title: "Curso de Fullstack Developer - Oracle Next Education (ONE)",
    descripcion:
      "Programa de formación intensiva de más de 700 horas, dividido en etapas ONE Tech Foundation y ONE Tech Advanced. Incluye IA, datos, backend y OCI.",
    enlace: "https://www.oracle.com/latam/education/oracle-next-education/",
  },
  {
    fecha: "2015",
    title: "Técnico Electromecánico - E.E.T. N°5 Dr. Salvador Debenedetti",
    descripcion:
      "Formación técnica en mantenimiento, reparación e instalación de sistemas electromecánicos, con conocimientos en PLCs, variadores y control industrial.",
    enlace:
      "https://www.escuelasargentinas.com/escuela-de-educacion-secundaria-tecnica-no5-dr-salvador-debenedetti-buenos-aires-061048300",
  },
]);

// Fondo dinámico según modo
const cardBackground = computed(() =>
  isDark.value ? "rgb(28, 41, 52)" : "#f9fafb"
);
</script>

<template>
  <div class="educacion-container">
    <div
      v-for="(item, index) in educacion"
      :key="index"
      class="card"
      :style="{ backgroundColor: cardBackground }"
    >
      <div
        class="fecha"
        :style="{
          backgroundColor: fechaColor[index % fechaColor.length].color,
          color: fechaColor[index % fechaColor.length].fg,
          borderColor: fechaColor[index % fechaColor.length].border,
        }"
      >
        {{ item.fecha }}
      </div>

      <div class="contenido">
        <h3 class="titulo">{{ item.title }}</h3>
        <p class="descripcion">{{ item.descripcion }}</p>
        <a :href="item.enlace" target="_blank" class="enlace">
          Ver más →
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.educacion-container {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  padding: 1rem;
}

/* Tarjeta */
.card {
  border-radius: 15px;
  padding: 1.5rem;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.card:hover {
  transform: scale(1.02);
}

/* Fecha */
.fecha {
  display: inline-block;
  padding: 0.4rem 1rem;
  border-radius: 10px;
  font-weight: bold;
  margin-bottom: 1rem;
  border: 2px solid transparent;
  text-align: center;
  font-size: 1rem;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.15);
}

/* Título */
.titulo {
  font-size: 1.4rem;
  font-weight: 700;
  margin-bottom: 0.6rem;
}

/* Descripción */
.descripcion {
  line-height: 1.6;
  font-size: 1rem;
  opacity: 0.9;
}

/* Enlace */
.enlace {
  display: inline-block;
  margin-top: 1rem;
  color: #69c5ff;
  font-weight: 600;
  text-decoration: none;
  transition: color 0.3s ease;
}

.enlace:hover {
  color: #fbca3e;
}

/* Responsivo */
@media (max-width: 768px) {
  .card {
    padding: 1rem;
  }

  .titulo {
    font-size: 1.2rem;
  }

  .descripcion {
    font-size: 0.95rem;
  }
}
</style>