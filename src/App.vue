<template>
<h1><center>EVALUACIÓN SESIÓN 4</center>
</h1>
  <div class="container">
    <div class="showcase">
      <MostrarImagenes msg="Welcome to Your Vue.js App"/>
    </div>
  </div>
</template>

<script>
import MostrarImagenes from './components/MostrarImagenes.vue'

export default {
  name: 'App',
  components: {
    MostrarImagenes
  }
}
</script>

<style>
* {
  box-sizing: border-box; /* Asegúrate de que el padding y el margen se incluyan en el ancho y alto total */
}

body {
  margin: 0;
  font-family: Arial, sans-serif; /* Cambia la fuente si es necesario */
}

.container {
  display: flex;
  justify-content: center; /* Centra el contenido horizontalmente */
  align-items: center; /* Centra el contenido verticalmente */
  min-height: 100vh; /* Asegúrate de que ocupe toda la altura de la ventana */
  background-color: tan; /* Color de fondo */
  padding: 20px; /* Espacio alrededor del contenido */
}

.showcase {
  max-width: 1080px; /* Ancho máximo del contenedor */
  width: 100%; /* Asegúrate de que ocupe el 100% del ancho permitido */
  background-color: white; /* Fondo blanco para el contenido */
  border-radius: 8px; /* Bordes redondeados */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Sombra para dar profundidad */
  padding: 20px; /* Espaciado interno */
}
</style>
