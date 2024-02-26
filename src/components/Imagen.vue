<template>
  <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="550"
    elevation="5"
    variant="tonal"
  >

  <template v-slot:loader="{ isActive }">
      <v-progress-linear
        :active="isActive"
        color="indigo-darken-4"
        height="4"
        indeterminate/>
    </template>
  
    <v-img
      cover
      height="250"
      :src="this.imagen"
      @load="this.loading = false"/>

    <v-card-item>
      <p class="text-indigo-darken-2"> {{ this.chiste.value }} </p>
      <!--<p class="text-right text-medium-emphasis"> {{ this.chiste.updated_at }}</p>-->

    </v-card-item>
    
    <v-divider class="mx-4 mb-1"/>

    <v-card-actions>
      <v-btn
        color="indigo-darken-4"
        variant="flat"
        @click="recargar"
        block rounded="XL"
        prepend-icon="mdi-dice-3"
      >
        Recargar
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
  export default {
    data: () => ({
      loading: false,
      imagen: "",
      chiste: {},
    }),

    mounted() {
      this.recargar()
    },

    methods: {
      recargar() {
        this.loading = true
        this.imagen = `https://picsum.photos/550/250?random=${Math.random()}`
        this.fetchChiste()
      },

      async fetchChiste() {
        try {
          const response = await fetch("https://api.chucknorris.io/jokes/random")

          if (response.ok) {
            this.chiste = await response.json()
          }
        } catch (error) {
          console.log(error)
        }
      },
    },
  }
</script>