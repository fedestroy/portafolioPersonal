<script setup>
import { inject } from 'vue';
const isDark = inject("theme");

// cambia el modo claro/oscuro
const toggleTheme = () => {
  isDark.value = !isDark.value;
  const theme = isDark.value ? "dark" : "light";
  document.documentElement.setAttribute("data-theme", theme);
  localStorage.setItem("theme", theme);
};
</script>

<template>
  <nav class="navbar">
    <ul class="nav-links">
      <li><a href="#top">Inicio</a></li>
      <li><a href="#educacion">Educación</a></li>
      <li><a href="#experiencia">Experiencia</a></li>
      <li><a href="#proyectos">Proyectos</a></li>
      <li><a href="#habilidades">Habilidades</a></li>
      <li><a href="#intereses">Intereses</a></li>
    </ul>

    <button class="theme-toggle" @click="toggleTheme">
      {{ isDark ? "☀️ Claro" : "🌙 Oscuro" }}
    </button>
  </nav>
</template>

<style scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  position: sticky;
  top: 0;
  z-index: 50;
  backdrop-filter: blur(10px);
  transition: background-color 0.4s ease;
}

/* Fondo según tema */
:deep(html[data-theme="light"]) .navbar {
  background-color: rgba(255, 255, 255, 0.8);
  color: #1a1a1a;
}

:deep(html[data-theme="dark"]) .navbar {
  background-color: rgba(20, 20, 20, 0.85);
  color: #f5f5f5;
}

/* Enlaces */
.nav-links {
  display: flex;
  gap: 1.5rem;
  list-style: none;
}

.nav-links a {
  font-weight: 600;
  text-decoration: none;
  color: inherit;
  transition: 0.3s;
}

.nav-links a:hover {
  color: #69C5FF;
}

/* Botón modo claro/oscuro */
.theme-toggle {
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  cursor: pointer;
  background: linear-gradient(90deg, #69C5FF, #FBCA3E);
  color: #000;
  font-weight: bold;
  transition: 0.3s;
}

.theme-toggle:hover {
  transform: scale(1.05);
}

/* Responsivo */
@media (max-width: 768px) {
  .nav-links {
    flex-wrap: wrap;
    gap: 1rem;
  }
  .theme-toggle {
    padding: 0.4rem 0.8rem;
    font-size: 0.9rem;
  }
}
</style>