<script setup>
import { ref, provide, onMounted } from 'vue';
import NavBar from './components/NavBar.vue';
import DatosPersonales from './components/DatosPersonales.vue';
import Educacion from './components/EducacionComponent.vue';
import ExperienciaComponente from './components/ExperienciaComponente.vue';
import ProyectosComponente from './components/ProyectosComponente.vue';
import HabilidadesComponente from './components/HabilidadesComponente.vue';
import InteresesComponente from './components/InteresesComponente.vue';

// Estado del tema (claro/oscuro)
const isDark = ref(false);
provide('theme', isDark);

// Al montar, recuperar tema previo y activar penalidad de clic derecho
onMounted(() => {
  // Restaurar tema desde localStorage
  const savedTheme = localStorage.getItem('theme');
  if (savedTheme === 'dark') {
    isDark.value = true;
    document.documentElement.setAttribute('data-theme', 'dark');
  }

  // Sistema de penalidad
  let penalidad = 0;
  document.addEventListener('contextmenu', (e) => {
    e.preventDefault();
    penalidad++;
    alert(`⚠️ Click derecho prohibido. Penalidad #${penalidad}`);
  });
});

// Cambiar tema y guardar preferencia
const toggleTheme = () => {
  isDark.value = !isDark.value;
  const theme = isDark.value ? 'dark' : 'light';
  document.documentElement.setAttribute('data-theme', theme);
  localStorage.setItem('theme', theme);
};
</script>

<template>
  <div :class="['app', isDark ? 'dark' : 'light']">
    <!-- Botón de modo claro/oscuro -->
    <button class="theme-toggle" @click="toggleTheme">
      {{ isDark ? "☀️ Modo Claro" : "🌙 Modo Oscuro" }}
    </button>

    <header id="top">
      <NavBar />
      <DatosPersonales />
    </header>

    <main>
      <section id="educacion">
        <h2 class="section-title">Educación - Cursos</h2>
        <Educacion />
      </section>

      <section id="experiencia">
        <h2 class="section-title">Experiencia</h2>
        <ExperienciaComponente />
      </section>

      <section id="proyectos">
        <h2 class="section-title">Proyectos</h2>
        <ProyectosComponente />
      </section>

      <section id="habilidades">
        <h2 class="section-title">Habilidades</h2>
        <HabilidadesComponente />
      </section>

      <section id="intereses">
        <h2 class="section-title">Intereses</h2>
        <InteresesComponente />
      </section>
    </main>

    <footer>
      <a href="#top">Volver arriba</a>
      <p>© 2025 Federico Nicolás Martínez - Portafolio personal</p>
    </footer>
  </div>
</template>

<style scoped>
/* 🎨 Transición entre temas */
.app {
  transition: background-color 0.4s ease, color 0.4s ease;
}

.app.light {
  background: var(--color-bg);
  color: var(--color-text);
}

.app.dark {
  background: var(--color-bg);
  color: var(--color-text);
}

/* 🌗 Botón modo claro/oscuro */
.theme-toggle {
  position: fixed;
  top: 1rem;
  right: 1rem;
  background: var(--color-accent);
  color: white;
  border: none;
  border-radius: 20px;
  padding: 0.6rem 1.2rem;
  cursor: pointer;
  font-weight: bold;
  box-shadow: 0 2px 10px rgba(0,0,0,0.2);
  transition: background 0.3s ease, transform 0.2s ease;
  z-index: 1000;
}
.theme-toggle:hover {
  background: #0056b3;
  transform: scale(1.05);
}

/* ⚓ Footer */
footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  font-size: 1.1rem;
}

/* 🏷 Títulos de sección */
.section-title {
  font-size: 2.2rem;
  font-weight: 800;
  text-transform: uppercase;
  text-align: center;
  margin: 3rem 0 2rem 0;
  letter-spacing: 1.5px;
  background: var(--color-accent-gradient);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  position: relative;
  text-shadow: 0 4px 12px rgba(105,197,255,0.3);
  transition: transform 0.3s ease;
}
.section-title:hover {
  transform: scale(1.05);
}
.section-title::after {
  content: "";
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 4px;
  background: var(--color-accent-gradient);
  border-radius: 2px;
}

/* 📱 Responsivo */
@media (max-width: 768px) {
  .section-title {
    font-size: 1.8rem;
  }
  .theme-toggle {
    top: 0.8rem;
    right: 0.8rem;
    padding: 0.5rem 1rem;
  }
}
</style>