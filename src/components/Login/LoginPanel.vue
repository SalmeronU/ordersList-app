<template>
    <div>
        <article class="LoginPanel">
            <h2>Iniciar sesión</h2>
            <v-form>
                <v-container>
                    <v-row>
                        <v-col cols="9" class="input">
                            <v-text-field
                                :dark="true"
                                color="FFF"
                                label="email"
                                required
                            >
                        </v-text-field>
                        </v-col>
                    </v-row>
                </v-container>

                <v-container>
                    <v-row>
                        <v-col cols="9" class="input">
                            <v-text-field
                            :dark="true"
                                type="password"
                                label="contraseña"
                                required>
                        </v-text-field>
                        </v-col>
                    </v-row>
                </v-container>

                <v-btn
                    elevation="2">Ingresar
                </v-btn>

            </v-form>
        </article>
    </div>
</template>

<script>
export default {
    
}
</script>

<style scoped>
    .LoginPanel{
        padding-top: 40%;
        background-color: rgb(33, 150, 243,0.8);
        text-align: center;
        height: 100vh;
        color:aliceblue;
    }

    .input{
        margin-left: 10%;
        text-align: center;
    }

    .registroLink{
        text-decoration: none;
        color: aliceblue;
    }
</style>