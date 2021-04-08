<template>
    <div>
        <v-row>
            <v-col lg="2" md="3" sm="12" xs="12">
                <orders-panel :nuevoProducto="nuevoProducto" @seleccionar-orden="enviarOrden"></orders-panel>
            </v-col>

            <v-col lg="5" md="6" sm="12" xs="12">
                <productos-panel :ordenActualizada="ordenSeleccionada"></productos-panel>
            </v-col>
            <v-col lg="5" md="6" sm="12" xs="12">
                <pago-panel @agregar-producto="agregarProducto" ></pago-panel>
            </v-col>
        </v-row>
    </div>
</template>

<script>
import OrdersPanel from '../components/Orders/OrdersPanel.vue';
import ProductosPanel from '../components/Orders/ProductosPanel.vue';
import PagoPanel from '../components/Orders/PagoPanel.vue';
export default {
    data(){
        return{
            ordenSeleccionada:null,
            nuevoProducto: ''
        };
    },
    components:{
        OrdersPanel,
        ProductosPanel,
        PagoPanel
    },
    methods:{
        enviarOrden(orden){
           this.ordenSeleccionada = orden; 
        },
        agregarProducto(name,price,sku,quantity){
            const nuevoProducto = {name:name,price:price,sku:sku,quantity:quantity};
            this.nuevoProducto = nuevoProducto;
        }
    }
}
</script>

<style scoped>
    
</style>