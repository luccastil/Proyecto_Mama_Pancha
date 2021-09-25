<template>
    <div id="CRUD">
        <v-card class="mx-auto my-15" max-width="400" text-center elevation="11">
            <v-card-subtitle class="pb-5 text-h5 font-weight-medium">Menú Admin</v-card-subtitle>
            <v-card-text class="text--primary mb-0">
                <v-form>
                    <div class="text-center">
                        <v-btn class="my-2" color="#00BFA5"  dark>Añadir producto
                        </v-btn>
                        <v-btn class="my-2" color="#00BFA5"  dark>Actualizar producto
                        </v-btn>
                        <v-btn class="my-2" color="#00BFA5"  dark>Buscar producto
                        </v-btn>
                        <v-btn class="my-2" color="#00BFA5"  dark>Eliminar producto
                        </v-btn>
                    </div>


                </v-form>
            </v-card-text>
            <v-card-actions class="d-flex justify-end">
                <v-btn class="subtitle-1 font-weight-bold" text @click="salir">SALIR</v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
export default {
    data: ()=>{
        return{

        }
    },

    methods: {
        salir(){
            console.log("Retornando Home");
            this.$router.push('/')
        },
    }
}
</script>

<style>

</style>