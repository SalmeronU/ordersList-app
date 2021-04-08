<template>
  <v-app>
    <div id="app">
    <Nav @mostrar-registro="updRegistro"/>
    <router-view :RegistroActivo="mostrarRegistro"/>
  </div>
  </v-app>
  
</template>


<script>
import Nav from './components/Nav';
export default {
  components: {Nav},
  data(){
    return{
      mostrarRegistro : false
    };
  },
  methods:{
      updRegistro(RegistroTrigger){
      this.mostrarRegistro = RegistroTrigger;
    }
  }
}
</script>
