<template>
  <div class="home">
    <Grilla :entidades="this.entidades"></Grilla>
  </div>
</template>

<script>
// @ is an alias to /src
import Grilla from '../components/Grilla.vue'

export default {
  name: 'Home',
  components: {
    Grilla
  },
  data(){
    return{
      entidades:[],      
    }

  },
  mounted(){
    this.getEntidades()
  },
  updated(){    
      this.getEntidades()    
    //ESTE METODO SE EJECUTA CONSTANTEMENTE Y NO LOGRO PREVENIRLO, POR ESO A VECES NO MUESTRA LA GRILLA Y HAY QUE ACTUALIZAR CON F5
  },
  methods:{
    
    async getEntidades() {
       
      if(this.$route.query.callingcode){
        //this.entidades = resJson.filter( entidad => entidad.codigo == this.$route.query.codigo)        
        const res = await fetch("https://restcountries.eu/rest/v2/callingcode/"+this.$route.query.callingcode);        
        const resJson = await res.json();       
        this.entidades = resJson
        console.log(this.entidades)         
        
        if(!res.ok){
          alert("El código ingresado no corresponde a ningún país valido")           
          this.$router.push(`/`);    
          
        }
        
      }
      else if(this.$route.query.region){
        const res = await fetch("https://restcountries.eu/rest/v2/region/"+this.$route.query.region);
        const resJson = await res.json();        
        this.entidades = resJson        
      }

    }
  }
}
</script>
