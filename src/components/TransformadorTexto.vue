.<!-- src/componentes/TransformadorTexto.vue -->
<template>
  <div class="card mt-4 rounded-5">
    <div class="card-body">
      <h2 class="card-title">Transformador de Texto</h2>
      <hr>
      <br>
      <br>
      <div class="form-group">
        <label for="textoInput"> <strong> <h3>Ingrese su texto:</h3></strong></label>
        <input
          type="text"
          id="textoInput"
          class="form-control"
          v-model="textoInput"
          @input="actualizarTransformaciones"
        />
      </div>
      
      <div class="mt-3">
        <p>Cantidad caracteres = {{ cantidadCaracteres }}</p>
        <p>1 - {{ textoCodificado }} (codificado)</p>
        <p>2 - {{ textoMayusculas }} (mayúscula)</p>
        <p>3 - {{ textoMinusculas }} (minúscula)</p>
        <p>4 - {{ textoAlternadoMayuscula }} (mayúscula / minúscula)</p>
        <p>5 - {{ textoAlternadoMinuscula }} (minúscula / mayúscula)</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TransformadorTexto',
  data() {
    return {
      textoInput: '',
      textoCodificado: '',
      textoMayusculas: '',
      textoMinusculas: '',
      textoAlternadoMayuscula: '',
      textoAlternadoMinuscula: ''
    };
  },
  computed: {
    cantidadCaracteres() {
      return this.textoInput.length;
    }
  },
  methods: {
    actualizarTransformaciones() {
      this.textoCodificado = this.codificarTexto(this.textoInput);
      this.textoMayusculas = this.textoInput.toUpperCase();
      this.textoMinusculas = this.textoInput.toLowerCase();
      this.textoAlternadoMayuscula = this.alternarMayusculas(this.textoInput, true);
      this.textoAlternadoMinuscula = this.alternarMayusculas(this.textoInput, false);
    },
    codificarTexto(texto) {
      const textoMin = texto.toLowerCase();
      return textoMin
        .split('')
        .map(letra => {
          switch (letra) {
            case 'a': return 'u';
            case 'e': return 'o';
            case 'o': return 'e';
            case 'u': return 'a';
            case 'i': return 'i';
            default: return letra;
          }
        })
        .join('');
    },
    alternarMayusculas(texto, empezarConMayuscula) {
      return texto
        .split('')
        .map((letra, indice) => {
          if (empezarConMayuscula) {
            return indice % 2 === 0 ? letra.toUpperCase() : letra.toLowerCase();
          } else {
            return indice % 2 === 0 ? letra.toLowerCase() : letra.toUpperCase();
          }
        })
        .join('');
    }
  }
};
</script>