<template>
    <div>
        <article class="OrdersContainer">
            <v-row v-if="ordenActualizada">
                <v-col lg="12" md="12" sm="12" xs="12">
                    <h3>Pedido: {{ordenActualizada.numero}}</h3>
                </v-col>
            </v-row>
            <v-row v-else>
                <v-col>
                    <h3>Sin ordenes para mostrar</h3>
                </v-col>
            </v-row>
        </article>
        <v-row>
            <v-col lg="12" md="12" sm="12" xs="12">
                <productocard :orden="ordenActualizada"></productocard>
            </v-col>
        </v-row>
    </div>
</template>

<script>
import Productocard from './ProductoCard.vue';
export default {
    props:['ordenActualizada'],
    components:{Productocard}
}
</script>

<style scoped>
    .OrdersContainer{
        padding-top: 2%;
        margin-top: 2%;
        margin-bottom: 2%;
        border-radius: 10px;
        font-weight: thin;
    }

    *{
      font-family: 'Roboto', sans-serif;
    }

    .infoPedido{
        font-size: small;
    }
</style>