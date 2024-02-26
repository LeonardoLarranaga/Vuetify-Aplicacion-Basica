<template>
    <v-table 
      fixed-header
      fluid style="height: 100vh;"
      >
      <thead>
        <tr>
          <th class="text-left font-weight-black">ID</th>
          <th class="text-left font-weight-black">Título</th>
          <th class="text-left font-weight-black">Estado</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in this.todos" :key="item.id">
          <td class="font-weight-black">{{ item.id }}</td>
          <td class="text-indigo-darken-2">{{ item.title }}</td>
          <td class="font-weight-medium" :style="{ color: item.completed ? '#689F38' : '#FBC02D' }">{{ item.completed ? "Completado" : "Pendiente" }}</td>
        </tr>
      </tbody>
    </v-table>
  </template>
  
  <script>
    export default {
      data: () => ({
        todos: {}
      }),

      mounted() {
        this.fetchToDos()
      },

      methods: {
        async fetchToDos() {
          try {
            const response = await fetch("https://jsonplaceholder.typicode.com/todos")

            if (response.ok) {
              this.todos = await response.json()
            }
          } catch (error) {
            console.log(error)
          }
        }
      }
    }
  </script>
  