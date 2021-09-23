<template>
    <div>
        <v-card color="grey lighten-4" flat height="200px" tile >
            <v-toolbar extended>

            <v-toolbar-title>
                <h1 class="logo__nombre no-margin centrar-texto" >Mama<span class="logo__bold">Pancha</span></h1>
            </v-toolbar-title>

            <v-spacer></v-spacer>

            <router-link class="link" to="/"><v-btn class="button" depressed elevation="3" plain> Productos </v-btn></router-link>
            <router-link class="link" to="/contacto"><v-btn class="button" depressed elevation="3" plain> Contacto </v-btn></router-link>
            <router-link class="link" to="/recomendados"><v-btn class="button" depressed elevation="3" plain> Recomendados </v-btn></router-link>
            <router-view/>

            </v-toolbar>
        </v-card>
    </div>
</template>
<script>
export default {
}
</script>
<style>

    h1 {
        font-family: 'Brush Script MT', cursiva;
        font-size: 3rem;
        margin-top: 3rem;
        font-weight: normal;
    }

    .button {
        text-align: center;
        margin: 1rem;
        margin-top: 5rem;
    }

    .logo__bold { 
        font-family: 'Calibri'; 
        font-weight: bold;
    }

    .link {
        text-decoration: none;
    }

</style>