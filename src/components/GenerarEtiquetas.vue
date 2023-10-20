   <template>
        <div class="modal-etiqueta" v-if="etiquetaData.length > 0">
          <div class="modal-content etiqueta-container ">
            
            <!-- Mostrar los datos de la etiqueta -->
            <div v-for="(pedido, index) in etiquetaData" :key="index">
                <div class="etiqueta">
              <div class="d-flex justify-content-between align-items-start">
                <div class="etiqueta-header">
                        <div class="col-12">
                  <h1 class="mb-1"><strong>Nº de Pedido: {{ pedido.numPedido }}</strong></h1>
                  <h3 class="alineado">Bulto {{index + 1}} de {{etiquetaData.length}}</h3>
                </div>
        </div>
                <div class="etiqueta-qr">
                  <vue-qr
                    :text="generarTextoQR(pedido, index+1, etiquetaData.length)"
                    :size="120"
                    class="qr"
                  ></vue-qr>
                </div>
              </div>
              <div class="etiqueta-info">
                <div class="col">
                  <p class="mb-1">{{ pedido.nombre }} {{ pedido.apellido }}</p>
                  <p class="mb-1">{{ pedido.direccion }}</p>
                  <p class="mb-1">{{ pedido.codigoPostal }} {{ pedido.ciudad }}</p>
                </div>
              </div>
              
                  <button @click="cerrarModalEtiqueta(pedido)">Cerrar</button>
            </div> 
            </div>
          </div>
        </div>
    </template>
    <!-- <div class="modal-etiqueta" v-if="etiquetaData.length > 0">
        <div class="modal-content etiqueta">
          <h2>Etiquetas</h2>
       
        <div v-for="(pedido, index) in etiquetaData" :key="index">
            
        <h3>Nº de Pedido: {{ pedido.numPedido }}</h3>
        <h5>Bulto {{ index+1 }}</h5>
        <p class="">{{ pedido.nombre }} {{ pedido.apellido }}</p>
        <p>  {{ pedido.direccion }}</p>
        <p>{{ pedido.codigoPostal }} {{ pedido.ciudad }}</p>
        
        <vue-qr
          :text="generarTextoQR(pedido, index+1, etiquetaData.length)"
          :size="200"
        ></vue-qr>
        <button @click="cerrarModalEtiqueta(pedido)">Cerrar</button>
      </div>
    </div>
</div> -->
  
  
  <script>
  import vueQr from "vue-qr/src/packages/vue-qr.vue";
  export default {
    props: {
      etiquetaData: Array,
    },
    components: {
    vueQr,
  },
    methods: {
      cerrarModalEtiqueta() {
        this.$emit('closeModalEtiqueta');
      },
      
      generarTextoQR(pedido,index) {
      // Construir la cadena para el código QR con la estructura especificada
      const cadenaQR = `${pedido.numPedido};${index};${pedido.bultosTotales};${pedido.nombre} ${pedido.apellido};${pedido.direccion};${pedido.codigoPostal};${pedido.ciudad}`;
      return cadenaQR;
    },
    },
  };
  </script>
  
 <style scoped>
 .etiqueta-container {
    max-width: 47rem; /* Ancho máximo de la etiqueta */
    margin: 0 auto; /* Centrar la etiqueta en la pantalla */
  }
  
  .etiqueta {
 
        background-color: #fff; /* Fondo blanco para la etiqueta */
        padding: 10px; /* Espaciado interno de la etiqueta */
        border: 2px solid #000; /* Borde negro de 2 píxeles */
        border-radius: 10px; /* Bordes redondeados de 10 píxeles */
      }
      
      /* Resto de tu estilo CSS existente */
      

  
  .etiqueta-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .etiqueta-qr {
    text-align: right;
   
  }
  
  .etiqueta-info {
    /* Alinea el contenido a la izquierda */
    text-align: left;
  }
.alineado{
    text-align: left;
}
  
</style> 