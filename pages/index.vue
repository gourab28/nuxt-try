<template>
  <p v-if="$fetchState.pending">Fetching mountains...</p>
  <p v-else-if="$fetchState.error">An error occurred :(</p>
  <div v-else>
    <h1>Nuxt Mountains</h1>
    <ul>
      <li v-for="mountain of mountains">{{ mountain.title }}</li>
    </ul>
    <v-alert
  color="#fff"
  elevation="2"
  type="warning"
  @click="$fetch">
      Refresh
    </v-alert>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        mountains: []
      }
    },
    async fetch() {
      this.mountains = await fetch(
        'https://jsonplaceholder.typicode.com/posts'
      ).then(res => res.json())
    }
  }
</script>
