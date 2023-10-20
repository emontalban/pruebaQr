<template>
  <div class="hello">
    <!-- ... Otro contenido ... -->

    <button @click="ejecutarMetodo">Abrir Modal</button>
    <ModalW v-if="showModal" @closeModal="showModal = false" @etiqueta-generada="mostrarEtiqueta" />

    <!-- Mostrar el componente Etiqueta cuando se prepara la etiqueta -->
    <GenerarEtiquetas v-if="etiquetaGenerada" :etiqueta="etiqueta" /> 
  </div>
</template>

<script>
import ModalW from './ModalW.vue';
import GenerarEtiquetas from './GenerarEtiquetas.vue';


export default {
  data() {
    return {
      showModal: false,
      etiquetaGenerada: false,
      etiqueta: {
        nombre: "",
        apellido: "",
        ciudad: "",
        numPedido: "",
        bulto: "",
        direccion: "",
        codigoPostal: "",
      },
    };
  },
  methods: {
    ejecutarMetodo() {
      this.showModal = true;
    },
    mostrarEtiqueta(datosEtiqueta) {
      this.etiquetaGenerada = true;
      this.etiqueta = datosEtiqueta;
    },
  },
  components: {
    ModalW,
    GenerarEtiquetas,
 
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
