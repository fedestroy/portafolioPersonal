<script setup>
//Este es un arreglo con ref para que se pueda reactivar al cambio de los intereses
import { ref } from 'vue'

const intereses = ref([
    'Soy programador en formación (UTN) con orientación al desarrollo fullstack con fuerte base en backend y conocimientos en Python, Java, JavaScript, HTML, CSS, MySQL y sistemas SIEM/IDS. ',
    'Me considero una persona curiosa, proactiva y apasionada por la tecnología y el desarrollo de software, complementando mi formación con cursos de Ciberseguridad (Google) y Desarrollo Full Stack (Oracle Next Education). ',
    'He desarrollado proyectos académicos y personales aplicando programación orientada a objetos (OOP), bases de datos SQL/NoSQL, API CRUD y dispositivos IoT (ESP32). ',
    'Busco mi primera oportunidad como Trainee o Junior Backend Developer / Full Stack Developer, donde pueda aplicar mis conocimientos, aprender nuevas tecnologías y contribuir al desarrollo de proyectos reales con compromiso, profesionalismo y entusiasmo. '

])
</script>

<template>
  <div class="intereses-contenedor">
    <ul class="contenedor-lista">
      <li class="item" v-for="interes in intereses" :key="interes">
        {{ interes }}
      </li>
    </ul>
  </div>
</template>
<style scoped>
.intereses-contenedor {
  display: flex;
  position: relative;
  margin: 0 auto;
  max-width: 100%;
  padding: 1.5rem;
  border-radius: 12px;
  overflow: hidden;
  /* nuevo fondo: degradado animado celeste -> amarillo */
  background: linear-gradient(45deg, #69C5FF 0%, #9EDFFF 45%, #FBCA3E 100%);
  background-size: 200% 200%;
  animation: interestGradient 10s ease infinite;
  box-shadow: 0 10px 30px rgba(7,32,58,0.12);
}

/* animación para desplazar el degradado */
@keyframes interestGradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.contenedor-lista {
  list-style-type: none;
  padding: 1rem;
  margin-bottom: .5rem;
  color: #041827; /* texto oscuro para buen contraste */
  font-size: 1.15rem;
  line-height: 1.6;
  text-shadow: 0 1px 0 rgba(255,255,255,0.12);
}

.item { margin-bottom: 1rem; }

/* ajustes responsivos */
@media (max-width: 600px) {
  .intereses-contenedor { padding: 1rem; }
  .contenedor-lista { font-size: 1rem; }
}
</style>
