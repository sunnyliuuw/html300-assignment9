<template>
  <section class="container bg-white">
    <h1>{{test}}</h1>
    <button v-on:click="greet">Greet</button>
  </section>
</template>


<script>
  import axios from 'axios'
  export default {
    data() {
      return {
         test: "Hello"
       }
     },
     created: function() {
       //http://www.omdbapi.com/?apikey=90fcc7de&t=2018
       this.test = "Hello Again one More time";
       axios.get(` https://swapi.co/api/people`)
       .then(response => {
         // JSON responses are automatically parsed.
         this.posts = response.data
         console.log(this.posts);
       })
       .catch(e => {
         this.errors.push(e)
       })
       .finally(() => this.loading =true)
     },
     methods: {
       greet: function() {
         this.test = "Hello Again";
       }
     }
   }
</script>

<style lang="css" scoped></style>
