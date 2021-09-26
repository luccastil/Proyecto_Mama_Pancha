<template>
    <div id="CRUD">
        <v-card class="mx-auto my-15" max-width="400" text-center elevation="11">
            <v-card-subtitle class="pb-5 text-h5 font-weight-medium">Menú Admin</v-card-subtitle>
            <v-card-text class="text--primary mb-0">
                <v-form>
<!--BOTÓN AÑADIR PRODUCTO-->
                    <v-row justify="center">
                        <v-dialog v-model="dialog" persistent max-width="600px">
                            <template v-slot:activator="{ on, attrs }">
                                <v-btn class="my-3" color="#00BFA5"  dark v-bind="attrs" v-on="on">
                                AÑADIR PRODUCTO
                                </v-btn>
                            </template>
                            <v-card>
                                <v-card-title><span class="text-h5">Agregar producto</span>
                                </v-card-title>
                                <v-card-text>
                                    <v-container>
                                        <v-row>
                                            <v-col cols="12" sm="6">
                                                <v-autocomplete :items="['Obleas', 'Solteritas', 'Arequipe con mora', 'Conservas de fruta']" label="Tipo de Producto" multiple></v-autocomplete>
                                            </v-col>
                                            <v-col cols="12" sm="6" md="4">
                                                <v-text-field label="Precio*" prefix="$" required></v-text-field>
                                            </v-col>
                                            <v-card-text>
                                                <v-text-field label="Descripción*" required></v-text-field>
                                            </v-card-text>
                                        </v-row>
                                        <v-row>
                                            <v-file-input
                                                :rules="rules"
                                                accept="image/png, image/jpeg,"
                                                placeholder="Elije una imagen"
                                                prepend-icon="mdi-camera"
                                                label="Imagen">
                                            </v-file-input>
                                        </v-row>
                                    </v-container>
                                    <small>*Todos los campos son requeridos</small>
                                </v-card-text>
                                <v-card-actions>
                                    <v-spacer></v-spacer>
                                    <v-btn color="#00BFA5" text @click="cerrar">Cerrar</v-btn>
                                    <v-btn color="#00BFA5" text @click="guardar">Guardar</v-btn>
                                </v-card-actions>
                            </v-card>
                        </v-dialog>
                    </v-row>
<!--BOTÓN BUSCAR PRODUCTO-->
                    <v-row justify="center">
                        <v-dialog v-model="dialog" persistent max-width="600px">
                            <template v-slot:activator="{ on, attrs }">
                                <v-btn class="my-3" color="#00BFA5"  dark v-bind="attrs" v-on="on">
                                BUSCAR PRODUCTO
                                </v-btn>
                            </template>
                            <v-card>
                                <v-card-title><span class="text-h5">Información del producto</span>
                                </v-card-title>
                                <v-card-text>
                                    <v-container>
                                        <v-row>
                                            <v-autocomplete :items="['Obleas', 'Solteritas', 'Arequipe con mora', 'Conservas de fruta']" label="Tipo de Producto" multiple></v-autocomplete>
                                        </v-row>
                                        <v-row>
                                            <v-col cols="12" sm="6">
                                                <v-dialog v-model="dialog" persistent max-width="600px">
                                                    <template v-slot:activator="{ on, attrs }">
                                                        <v-btn class="my-3" color="#00BFA5"  dark v-bind="attrs" v-on="on">
                                                        ACTUALIZAR PRODUCTO
                                                        </v-btn>
                                                    </template>
                                                    <v-card>
                                                        <v-card-title><span class="text-h5">Agregar producto</span>
                                                        </v-card-title>
                                                        <v-card-text>
                                                            <v-container>
                                                                <v-row>
                                                                    <v-col cols="12" sm="6">
                                                                        <v-autocomplete :items="['Obleas', 'Solteritas', 'Arequipe con mora', 'Conservas de fruta']" label="Tipo de Producto" multiple></v-autocomplete>
                                                                    </v-col>
                                                                    <v-col cols="12" sm="6" md="4">
                                                                        <v-text-field label="Precio*" prefix="$" required></v-text-field>
                                                                    </v-col>
                                                                    <v-card-text>
                                                                        <v-text-field label="Descripción*" required></v-text-field>
                                                                    </v-card-text>
                                                                </v-row>
                                                                <v-row>
                                                                    <v-file-input
                                                                        :rules="rules"
                                                                        accept="image/png, image/jpeg,"
                                                                        placeholder="Elije una imagen"
                                                                        prepend-icon="mdi-camera"
                                                                        label="Imagen">
                                                                    </v-file-input>
                                                                </v-row>
                                                            </v-container>
                                                            <small>*Todos los campos son requeridos</small>
                                                        </v-card-text>
                                                        <v-card-actions>
                                                            <v-spacer></v-spacer>
                                                            <v-btn color="#00BFA5" text @click="cerrar">Cerrar</v-btn>
                                                            <v-btn color="#00BFA5" text @click="guardar">Guardar</v-btn>
                                                        </v-card-actions>
                                                    </v-card>
                                                </v-dialog>
                                            </v-col>
                                            <v-col cols="12" sm="6">
                                                <v-btn class="my-3" color="#00BFA5" dark @click="cerrar">ELIMINAR PRODUCTO
                                                </v-btn>
                                            </v-col>
                                        </v-row> 
                                    </v-container>
                                </v-card-text>
                                <v-card-actions>
                                    <v-spacer></v-spacer>
                                    <v-btn color="#00BFA5" text @click="cerrar">Cerrar</v-btn>
                                    <v-btn color="#00BFA5" text @click="guardar">Guardar</v-btn>
                                </v-card-actions>
                            </v-card>
                        </v-dialog>
                    </v-row>
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
    data: () => ({
        rules: [
            value => !value || value.size < 2000000 || 'Avatar size should be less than 2 MB!',
        ],
    }),
    methods: {
        salir(){
            console.log("Retornando Home");
            this.$router.push('/')
        },
        cerrar(){
            console.log("Retornando Home");
            this.$router.push('/Login')
        },
        guardar(){
            console.log("Retornando Home");
            this.$router.push('/Login')
        },
    }
}
</script>

<style>

</style>