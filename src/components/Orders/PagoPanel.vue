<template>
    <div class="pagoContainer">
        <p>¿Agregar algo a la orden?</p>
        <v-form
        ref="agregarProductoForm"
        v-model="valid"
        >
            <v-row>
            <!-- Name input -->
            <v-col lg="3">
                <v-text-field
                required
                v-model="name"
                :rules="campoVacio"
                label="Producto"
                >

                </v-text-field>
            </v-col>
            <!-- Price input -->
            <v-col lg="3">
                <v-text-field
                v-model="price"
                :style="{textAlign: 'center'}"
                :rules="campoVacio"
                label="Precio"
                >

                </v-text-field>
            </v-col>
            <!-- SKU input -->
            <v-col lg="3">
                <v-text-field
                v-model="sku"
                :rules="campoVacio"
                label="SKU"
            >
                </v-text-field>
            </v-col>
        </v-row>

        <v-row>
            <!-- Quantity input -->
            <v-col lg="3">
                <v-text-field
                :style="{textAlign: 'center'}"
                v-model="quantity"
                type="number"
                label="Cantidad"
                :rules="mayorZero"
                :outlined="true"
                >
    
                </v-text-field>
            </v-col>
            <!-- Agregar a orden BTN -->
            <v-col lg="2">
                <v-btn
                @click="agregarProducto"
                 :style="{backgroundColor: '#2196F3',color:'white',marginTop: '10%',width:'150%'}">
                    <v-icon>mdi-content-save</v-icon>
                </v-btn>
            </v-col>
        </v-row>
        </v-form> 
        <v-row>
            <!-- Pagar BTN -->
            <v-col lg="3">
                <v-spacer></v-spacer>
            </v-col>
            <v-col lg="3">
                <v-btn :style="{backgroundColor:'#FFEB3B',color:'#2196F3'}">
                    Proceder al pago
                    <v-icon>
                        mdi-cash-register
                    </v-icon>
                </v-btn>
            </v-col>
            <v-col lg="3">
                <v-spacer></v-spacer>
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    data(){
        return{
            valid: true,
            name:'',
            campoVacio: [
                v => v.length>0 || 'Campo faltante',
            ],
            mayorZero: [
                v => v>0 || 'Al menos una pieza',
            ],
            price:'',
            sku:'',
            quantity:''
        };
    },
    methods:{
        agregarProducto(){
            if(this.$refs.agregarProductoForm.validate()){
                this.$emit('agregar-producto',this.name,this.price,this.sku,this.quantity);
                this.name='';
                this.price='';
                this.sku='';
                this.quantity=''; 
                this.$refs.agregarProductoForm.resetValidation()
            }
        },
    }
}
</script>

<style scoped>
    .pagoContainer{
        box-shadow: 0px 2px 08px rgb(0,0,0,0.36);
        margin-top: 9%;
        border-radius: 2px;
        padding-top: 5%;
        padding-left: 5%;
    }

    *{
        font-family: 'Roboto', sans-serif;
    }

</style>