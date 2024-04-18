<script>
import { store } from '../store.js';
import Card from './Card.vue';
export default {
  components:{
    Card,
  },
  data(){
    return {
      store: store
    }
  }
}
</script>

<template>


  <section>
    <div class="container">

      <h2>Movies</h2>
      <ul v-if="store.movies.length !==0">
        <Card v-for="movie in store.movies" :key="movie.id" :item="movie"/>

      </ul>
      <p v-else>Nessun risultato nella ricerca</p>
    </div>


    <div class="container">
      <h2>tvs</h2>
      <ul v-if="store.tvs.length !==0">
        <Card v-for="tv in store.tvs" :key="tv.id" :item="tv"/>
      </ul>
    </div>
  </section>

</template>

<style lang="scss"></style>
