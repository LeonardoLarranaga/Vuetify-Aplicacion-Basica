<template>
    <v-layout fluid style="height: 100vh;">
      <v-app-bar :elevation="2.5" rounded>
        <v-app-bar-title>Aplicación Básica: Imágenes, Chistes & To-dos</v-app-bar-title>
      </v-app-bar>

      <v-navigation-drawer expand-on-hover rail :width="275">
        <v-list>
          <v-list-item 
            prepend-icon="mdi-home"
            title="Home"
            subtitle="Welcome to Vuetify"
            link to="/"
          ></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item 
            prepend-icon="mdi-tooltip-image" 
            title="Imagen & Chiste" 
            link to="/imagen"
          ></v-list-item>

          <v-list-item 
            prepend-icon="mdi-order-bool-ascending-variant" 
            title="To-Dos" 
            link to="/tabla"
          ></v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-main><router-view/></v-main>

    </v-layout>
</template>

<script setup>
//
</script>
