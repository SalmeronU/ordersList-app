<template>
    <div>
        <article class="OrdersContainer">
            <!-- <h3>ORDENES DE COMPRA</h3> -->
            <v-row>
                <v-col lg="10" class="buscadorOrden">
                    <v-text-field
                    v-model="ordenBuscada"
                    append-icon="mdi-card-search"
                    :dark="false"
                    label="Buscar número de orden..."
                    :outlined="true"
                    >
                    </v-text-field>
                </v-col>
            </v-row>

            <v-row v-if="ordenBuscada === ''" :style="{maxHeight: '78vh',overflowY:'auto'}">
                <v-col lg=12>
                    <v-tabs :active-class="'activeTab'" class="tabs"
                    :vertical="true"
                    >
                         <v-tab @click="seleccionarOrden(orden)"
                          v-for="orden in Ordenes" :key="orden.numero">
                            Número de pedido: {{orden.numero}}
                        </v-tab>
                    </v-tabs>
                </v-col>    
            </v-row>

            <v-row v-else>
                <v-col lg=12>
                    <v-tabs :active-class="'activeTab'"
                    :vertical="true"
                    >
                         <v-tab v-if="ordenEncontrada.numero === 'NF'">
                            Número de orden no existente
                        </v-tab>
                        <v-tab v-else>
                            Número de orden: {{ordenEncontrada.numero}}
                        </v-tab>
                    </v-tabs>
                </v-col>    
            </v-row>
        </article>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    props:['nuevoProducto'],
    data(){
        return{
            Ordenes:[
                {numero:'5555',productos:[{sku:'5466',name:'Nintendo Switch',quantity:1,price:7999.00},{sku:'5466',name:'Xbox one s',quantity:1,price:5999.00},{sku:'5466',name:'Playstation 5',quantity:1,price:7999.00},{sku:'5466',name:'Nintendo Wii ',quantity:1,price:5999.00},{sku:'5466',name:'Xbox 360',quantity:1,price:7999.00},{sku:'5466',name:'Xbox one',quantity:1,price:5999.00},{sku:'5466',name:'Nintendo 64',quantity:1,price:7999.00},{sku:'5466',name:'Nintendo DS',quantity:1,price:5999.00}]},
                {numero:'4586',productos:[{sku:'7899',name:'Autolavado Hot Wheels',quantity:1,price:578.00},{sku:'5466',name:'Mustang Hot Wheels',quantity:1,price:47.00}]},
                {numero:'9813',productos:[{sku:'3562',name:'iPad Mini',quantity:2,price:5499.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'9813',productos:[{sku:'3562',name:'iPad Mini',quantity:2,price:5499.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
                {numero:'1688',productos:[{sku:'4856',name:'Beats by Dre',quantity:4,price:2400.00}]},
            ],
            ordenBuscada:'',
            ordenEncontrada:'',
        }
    },
    methods:{
        seleccionarOrden(orden){
            this.ordenEncontrada = orden;
            this.$emit('seleccionar-orden', this.ordenEncontrada);
        }
    },
    mounted(){
        axios({
            method:'GET',
            url:'https://eshop-deve.herokuapp.com/api/v2/orders', 
            headers:{
                Authorization: 'eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJwUGFINU55VXRxTUkzMDZtajdZVHdHV3JIZE81cWxmaCIsImlhdCI6MTYwNTY0NDA0NzA1OH0.skfIY_7CAANkxmhoq37OI4jYRE8flx1ENq1v1VaRevJiroYNFQYz7Oy6hL1YZ1OJkevXSQFuLMHTqY0w6d5nPQ'
            }
        }).then(response =>{
            console.log(response);
        });
        this.ordenEncontrada = this.Ordenes[0];
        this.$emit('seleccionar-orden', this.ordenEncontrada);
    },
    watch:{
        ordenBuscada(actual){
            const ordenFiltrada= this.Ordenes.find(orden => orden.numero === actual);
            ordenFiltrada ? this.ordenEncontrada = ordenFiltrada : this.ordenEncontrada = {numero:'NF', productos:{}};
        },
        nuevoProducto(nuevo){
            this.Ordenes.find(orden => { 
                orden.numero === this.ordenEncontrada.numero ? orden.productos.push(nuevo) : ''
            });
            
        }
            
    }
}
</script>

<style scoped>
    .OrdersContainer{
        box-shadow: 0px 2px 08px rgba(0, 0, 0, 0.26);
        text-align: center;
        /* background-color: rgba(223, 143, 78, 0.9); */
        color: black;
        padding-top: 6%;
    }

    *{
      font-family: 'Roboto', sans-serif;
    }
    .buscadorOrden{
        margin-left: 8%;
        margin-top: 2%;
    }
    .activeTab{
        background-color: rgb(79, 80, 77);
        color: aliceblue;
    }

     ::-webkit-scrollbar{
        width: 10px;
    }
    ::-webkit-scrollbar-track {
      box-shadow: inset 0 0 5px grey; 
      border-radius: 5px;
    }

    ::-webkit-scrollbar-thumb {
      background-color: rgb(79, 80, 77,0.5); 
      border-radius: 5px;
    }
</style>