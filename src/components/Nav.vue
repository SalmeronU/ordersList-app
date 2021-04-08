<template>
    <v-app-bar color="#2196F3">
      <v-img src="@/assets/Tendencys.png"
      max-height="50"
      max-width="200"
      >   
      </v-img>


    <v-tabs color="yellow" align>
        <v-spacer></v-spacer>
        <v-tab v-for="tab in tabs" :key="tab" class="Hola" @click="activeTab(tab)">{{tab}}</v-tab>
        <v-tab @click="mostrarRegistro">Registro</v-tab>
    </v-tabs>
    </v-app-bar>
</template>

<script>
export default {
    data(){
        return{
            tabs: [
                'Ingresar',
                'Ordenes'
            ],
        };
    },
    methods:{
        activeTab(tab){
            this.$emit('mostrar-registro',false);
            this.$router.push('/'+tab);
        },
        mostrarRegistro(){
            this.$route.path === '/Ordenes' ? this.revisarRuta()  : this.$emit('mostrar-registro',true);    
        },
        revisarRuta(){
            this.$emit('mostrar-registro',true);
            this.$router.push('/Ingresar');
        }
    }
}
</script>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');

  *{
      font-family: 'Roboto', sans-serif;
      color: #FFEB3B;
  }


</style>
