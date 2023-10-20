<template>
    <div>
        <label> Introduce la url</label><br/>
        <input type="text" v-model ="urlPagina"><br/>
        <label>En el caso de querer un logo en el centro</label><br/>
        <input type="text" v-model ="urlLogo"><br/>
        <br/>
        <vue-qr :logoSrc="this.urlLogo"
        :text="this.urlPagina"
        :size="200"
        dotScale ="1"></vue-qr>
        <br/>
    </div>

</template>
<script>


/******************************************************************************************/
import vueQr from "vue-qr/src/packages/vue-qr.vue"

export default{
    name:"GenerarQr",
    data(){
        return {
            urlLogo:"",
            urlPagina:""
        }
    },
    components:{
        vueQr
    }
}
/***********************************************************************************************/
</script>
