<template>
    <div>
        <v-row v-if="orden" :style="{maxHeight: '82vh',overflowY:'auto'}">
            <v-col data-aos="fade-in" v-for="producto in orden.productos" :key="producto.name" lg="12">
                <div class="productoContainer">
                    <!-- HEADER DE LA CARD -->
                    <div class="containerHeader">
                        <v-row>
                            <v-col lg="3">
                            PEDIDO REALIZADO<br>{{fechaPedido}}
                        </v-col>
                        <v-col lg="3">
                            TOTAL<br>${{producto.price*producto.quantity}}
                        </v-col>
                        <v-col lg="3">
                            ENTREGAR A<br>Ulises Salmerón
                        </v-col>
                        </v-row>
                    </div>
                    <div class="containerContent">
                    </div>

                    <!-- CONTENIDO DE LA CARD -->
                    <div class="containerContent">
                        <v-row >
                        <v-col lg="3">
                            <img src="https://http2.mlstatic.com/D_Q_NP_2X_650220-MLM43775063315_102020-AB.webp" alt="">
                        </v-col>
                        <v-col lg="3">
                            <p><a href="#">{{producto.name}}</a>
                            <br>
                            Precio: ${{producto.price}}</p>
                        </v-col>
                        <v-col lg="3">
                            <p>SKU: {{producto.sku}} <br> Stock: Existente</p>
                        </v-col>
                        <v-col lg="3">
                            <p class="cantidadProducto">Cantidad: {{producto.quantity}}</p>
                            <v-btn
                            @click="updQuantity('rmv',producto)"
                            :style="{backgroundColor: 'red', color:'white'}"
                             icon>
                                <v-icon dark>
                                    mdi-minus
                                </v-icon>
                            </v-btn>
                            <v-btn
                            @click="updQuantity('add',producto)"
                            :style="{backgroundColor: 'green',color:'white'}"
                             icon>
                                <v-icon>
                                    mdi-plus
                                </v-icon>
                            </v-btn>
                        </v-col>
                    </v-row>
                    </div>
                </div>
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    data(){
        return{
            fechaPedido: ''
        };
    },
    mounted(){
        const fecha = new Date();
        const hoy = fecha.getFullYear()+'-'+(fecha.getMonth()+1)+'-'+fecha.getDate()
        this.fechaPedido = hoy;
    },
    methods:{
        updQuantity(accion,producto){
            accion === 'add' ? producto.quantity++ : producto.quantity--;
        }
    },
    props:['orden']
}
</script>

<style scoped>
    .productoContainer{
        border-radius: 5px;
        box-shadow: 0px 2px 08px rgb(0,0,0,0.26);
        margin-bottom: 3%;
    }

    .productoContainer:hover{
        cursor: pointer;
    }

    .containerHeader{
        background-color: #4F504D;
        padding-left: 2%;
        color: white;
        border-radius: 5px 5px 0 0;
        font-size: x-small;
    }

    .containerContent{
        height: fit-content;
        font-size: small;
        padding-left: 5%;
        padding-top: 1%;
    }

     .containerContent img{
         width: 100%;
    }   

      .containerContent p,a{
         margin-top: 13%;
    } 

    ::-webkit-scrollbar{
        width: 10px;
    }
    ::-webkit-scrollbar-track {
      box-shadow: inset 0 0 5px grey; 
      border-radius: 5px;
    }

    ::-webkit-scrollbar-thumb {
      background-color: rgb(33, 150, 243,0.5); 
      border-radius: 5px;
    }
</style>