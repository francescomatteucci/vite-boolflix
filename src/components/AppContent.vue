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
      <div class="row">
        <div class="col-md-6">
          <h2>Movies</h2>
          <ul v-if="store.movies.length !== 0" class="list-unstyled d-flex flex-wrap">
            <Card v-for="movie in store.movies" :key="movie.id" :item="movie" />
          </ul>
          <p v-else>Vai alla ricerca del tuo film preferito!</p>
        </div>
        <div class="col-md-6">
          <h2>TV Shows</h2>
          <ul v-if="store.tvs.length !== 0" class="list-unstyled d-flex flex-wrap">
            <Card v-for="tv in store.tvs" :key="tv.id" :item="tv" />
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>


<style lang="scss">
section p {
  background-color: lightgrey;
  border: 1px transparent gray;
  border-radius: 4px;
}

.container{
  width:100%;
}

.row{
  display:flex;
  flex-wrap: nowrap;
}

.col-4{
  width: calc(100% / 12 * 3);
}


</style>
