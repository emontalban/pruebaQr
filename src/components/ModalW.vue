<template>
  <div class="modal">
    <div class="modal-content">
      <!-- Contenido del modal -->
      <h2>Contenido del Modal</h2>
      <!-- Otros elementos del modal -->

      <!-- Botón "Preparar" -->
      
      <button @click="generarEtiqueta">Preparar</button>



      <!-- Agregar un nuevo modal (ModalEtiqueta) para mostrar la etiqueta -->
      <GenerarEtiquetas v-if="mostrarModalEtiqueta" @closeModalEtiqueta="mostrarModalEtiqueta = false" :etiquetaData="etiquetaData" />
    </div>
  </div>
</template>

<script>
import GenerarEtiquetas from './GenerarEtiquetas.vue';

export default {
  components: {
     GenerarEtiquetas, 
    },
  data() {
    return {
      mostrarModalEtiqueta: false,
      etiquetaData: [],
    };
  },
    methods: {
        generarEtiqueta() { 
          const pedidos = [
        {
          nombre: "John",
          apellido: "Doe1",
          ciudad: "Ciudad Ejemplo",
          numPedido: "primero",
          bulto: "1",
          direccion: "La calle de al lado1",
          codigoPostal: "45685",
        },
        {
          nombre: "Pepe",
          apellido: "Doe2",
          ciudad: "Ciudad Ejemplo",
          numPedido: "segundo",
          bulto: "1",
          direccion: "La calle de al lado2",
          codigoPostal: "45685",
        },
        {
          nombre: "juan",
          apellido: "Doe3",
          ciudad: "Ciudad Ejemplo3",
          numPedido: "tercero",
          bulto: "1",
          direccion: "La calle de al lado",
          codigoPostal: "45685",
        },
        // Agregar más pedidos aquí
      ];
     // Calcular el número total de bultos automáticamente
    const numeroTotalBultos = pedidos.length;

// Asignar el número total de bultos a cada pedido
pedidos.forEach((pedido) => {
  pedido.bultosTotales = numeroTotalBultos;
});
            // Coloca aquí la lógica para realizar la acción "Preparar"
            // Por ejemplo, puedes emitir un evento para que lo maneje el componente padre
            this.etiquetaData =pedidos;

              // Mostrar el nuevo modal (ModalEtiqueta)
      this.mostrarModalEtiqueta = true;
        },
    },
    
};
</script>

<style scoped>
/* Estilos del modal */
.modal {
  /* Estilos para el fondo del modal */
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  /* Estilos para el contenido del modal */
  background: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}
</style>
