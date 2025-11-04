<script setup>
import { ref } from 'vue'
//ref es una función que se utiliza para crear una referencia reactiva en Vue 3
var misProyectos = ref([]);

//.value es una propiedad que se utiliza para acceder al valor de una referencia reactiva en Vue 3
misProyectos.value = ([
    //Esto es un array de objetos que contiene información sobre los proyectos
    {
        id: 1,
        src: "/src/assets/pro2.png",
        titulo: "Agenda telefónica (Python)",
        descripcion: " Aplicación CRUD con menú para alta, baja, modificación y consulta de contactos.  ",
        projectLink: "https://github.com/fedestroy/agenda_telefonica",
        githubLink: "https://github.com/fedestroy/agenda_telefonica"
    },
    {
        id: 2,
        src: "/src/assets/pro4.png",
        titulo: "Juego adivinar el numero secreto",
        descripcion: "Juego programado en .JavaScript, .HTML y .CSS",
        projectLink: "https://github.com/fedestroy/juego-numero-secreto",
        githubLink: "https://github.com/fedestroy/juego-numero-secreto"
    },
    {
        id: 3,
        src: "/src/assets/pro1.png",
        titulo: "Estación meteorológica (IoT)",
        descripcion: "Proyecto en Python + electrónica ESP32 para capturar y enviar datos meteorológicos. (Tecnologías: Python, sensores IoT, comunicación serial, electrónica básica)",
        projectLink: "https://github.com/fedestroy/",
        githubLink: "https://github.com/fedestroy/"
    },
    {
        id: 4,
        src: "/src/assets/pro3.png",
        titulo: "Sistema de stock y ventas (Java)",
        descripcion: "CRUD de productos con simulación de facturación en consola. (Tecnologías: Java, POO, SQL, manejo de excepciones, estructuras de datos)",
        projectLink: "https://github.com/fedestroy/",
        githubLink: "https://github.com/fedestroy/"
    },
   
    
])
</script>
<template>
    <!-- Aquí va el código HTML de la galería de proyectos -->
    <div class="galeria">
        <!-- Itera sobre cada proyecto en la lista de misProyectos -->
        <!-- :key es una propiedad especial que se utiliza para identificar de forma única cada elemento en una lista de Vue.js -->
        <li class="proyecto" v-for="proyecto in misProyectos" :key="proyecto.id">
            <!-- Muestra la imagen del proyecto utilizando v-bind que es una directiva de enlace de atributo en Vue.js -->
            <img :src="proyecto.src" :alt="proyecto.titulo" />
            <div class="proyecto-info">
                <!-- Muestra el título y la descripción del proyecto utilizando la interpolación de Vue.js -->
                <h3>{{ proyecto.titulo }}</h3>
                <p>{{ proyecto.descripcion }}</p>
                <div class="proyecto-links">
                    <a :href="proyecto.projectLink" class="btn-ver-mas" target="_blank" rel="noopener noreferrer">Ver Proyecto</a>
                    <a :href="proyecto.githubLink" class="github-link" target="_blank" rel="noopener noreferrer">Ver Código en GitHub</a>
                </div>
            </div>
        </li>
    </div>
</template>

<style scoped>
.galeria {
  width: 100%;
  min-height: 100%;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  padding: 20px;
  justify-content: center;
  background-color: var(--color-background);
  transition: background-color 0.4s ease, color 0.4s ease;
}

.proyecto {
  display: flex;
  flex-direction: column;
  border: 1px solid var(--color-border);
  border-radius: 8px;
  overflow: hidden;
  background-color: var(--color-background-soft);
  flex: 1 1 280px;
  max-width: 300px;
  transition: background-color 0.4s ease, transform 0.3s ease;
}

.proyecto:hover {
  transform: translateY(-5px);
}

.proyecto img {
  width: 100%;
  height: auto;
  display: block;
}

.proyecto-info {
  padding: 15px;
  text-align: center;
}

.proyecto-info h3 {
  margin: 10px 0;
  font-size: 1.2em;
  color: var(--color-heading);
}

.proyecto-info p {
  margin: 10px 0;
  font-size: 1em;
  color: var(--color-text);
}

.proyecto-links {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 10px;
}

.proyecto-links .btn-ver-mas {
  background-color: #007BFF;
  color: #fff;
  padding: 10px 15px;
  border-radius: 5px;
  text-decoration: none;
  transition: background-color 0.3s;
}

.proyecto-links .btn-ver-mas:hover {
  background-color: #0056b3;
}

.proyecto-links .github-link {
  color: var(--color-text);
  text-decoration: none;
  font-size: 0.9em;
}

.proyecto-links .github-link:hover {
  text-decoration: underline;
}
</style>