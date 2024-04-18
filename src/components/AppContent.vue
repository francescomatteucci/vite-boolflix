<script>
import { store } from '../store.js';
import Card from './Card.vue';
export default {
  components: {
    Card,
  },
  data() {
    return {
      store: store
    }
  }
}
</script>

<template>
  <section>
    <div class="container">
      <div class="row d-flex">
        <div class="">
          <h2>Movies:</h2>
          <ul v-if="store.movies.length !== 0" class="layout">
            <Card v-for="movie in store.movies" :key="movie.id" :item="movie" />
          </ul>
          <p v-else>Vai alla ricerca del tuo film preferito!</p>
        </div>
        <div>
          <h2>TV Shows:</h2>
          <ul v-if="store.tvs.length !== 0" class="layout">
            <Card v-for="tv in store.tvs" :key="tv.id" :item="tv" />
          </ul>
          <p v-else>Vai alla ricerca della tua serie preferita!</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss">

.layout{
  display: flex;
  flex-wrap: wrap;

}

h2{
  color: white;
  padding-top: 20px;
  padding-bottom: 20px;
  padding-left: 10px;

}

</style>
