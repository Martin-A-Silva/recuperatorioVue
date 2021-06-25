<template>
  <div>
    <detalle-articulo :articulo="entidad"></detalle-articulo>
  </div>
</template>

<script>
import detalleArticulo from "../components/DetalleArticulo.vue";

export default {
  components:{
    detalleArticulo
  },
  data(){
    return{
      entidad: {}
    }
  },
  mounted(){
    this.getEntidad()    
  },
  updated(){
    //this.getEntidad()
  },
  methods:{
    async getEntidad() {
      const res = await fetch("https://restcountries.eu/rest/v2/name/"+this.$route.params.nombre);
        const resJson = await res.json();
        
        this.entidad = resJson[0]
        console.log(this.entidad)
    }
  }
}
</script>

<style>

</style>