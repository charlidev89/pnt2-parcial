<template>
  <div class="container mt-5">

    <div class="alert alert-success mt-3 rounded-3">
      <h1 class="mb-2">PNT2 - Parcial</h1>
    </div>

  </div>

  <div class="container mt-5">

    <TransformadorTexto />
    <RespuestasQuiz />
  </div>
  <footer class="bg-dark text-white text-center py-2  fixed-bottom">
    <div class="container">
      <div class="row">
        <div class="col-md-6">
          <h5>PNT2 - Parcial</h5>
          <p class="mb-0">App de transformación de texto con Vue.js Cli + Vite + Bootstrap</p>
        </div>
        <div class="col-md-6 text-md-end">
          <p class="mb-0">© Hecho por Carlos Arteaga 🚀</p>
          <p class="mb-0">Materia: PNT2 </p>
          <p class="mb-0">Profesor: Daniel Sanchez </p>

        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import TransformadorTexto from './components/TransformadorTexto.vue'
import RespuestasQuiz from './components/RespuestasQuiz.vue'

export default {
  name: 'App',
  components: {
    TransformadorTexto,
    RespuestasQuiz
  }
}
</script>

<style scoped>
h1 {
  color: rgb(66, 65, 71);
}
</style>