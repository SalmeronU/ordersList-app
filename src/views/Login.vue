<template>
    <div>
        <video-bg :sources="[require('@/assets/bg.mp4')]">
            <v-row v-if="!RegistroActivo" data-aos="zoom-in">
                    <v-col lg="3" sm="12" md="6" xs="12">
                        <login-panel></login-panel>
                    </v-col>
            </v-row>
            <v-row v-else>
                    <v-col lg="3" sm="12" md="6" xs="12">
                        <registro-panel></registro-panel>
                    </v-col>
            </v-row>
        </video-bg>

        
    </div>
</template>

<script>
import LoginPanel from '../components/Login/LoginPanel.vue'
import RegistroPanel from '../components/Registro/RegistroPanel.vue'
import VideoBg from 'vue-videobg'
export default {
    components:{LoginPanel,VideoBg,RegistroPanel},
    props: ['RegistroActivo']
}
</script>

<style scoped>
    *{
        font-family: 'Roboto', sans-serif;
    }
</style>