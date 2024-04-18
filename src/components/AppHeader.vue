<template>
    <header>
        <div class="container">
            <div><img
                    src="../assets/png-clipart-netflix-logo-netflix-logo-icons-logos-emojis-tech-companies-thumbnail-removebg-preview.png"
                    alt="">
                <ul>
                    <li>Home</li>
                    <li>Serie Tv</li>
                    <li>Film</li>
                    <li>Originali</li>
                </ul>
            </div>
            <div>
                <input type="text" v-model="query" placeholder="Cerca un film o serie tv">
                <button @click="fetchData">Cerca</button>
            </div>
        </div>

    </header>
</template>

<script>

import axios from 'axios';
import { store } from '../store.js'
export default {
    data() {
        return {
            query: '',
            store: store,
        }
    },
    methods: {
        fetchData() {
            console.log(this.query)
            console.log('recupero i dati di film')
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                    query: this.query
                }
            }).then((res) => {
                console.log(res.data.results)
                this.store.movies = res.data.results
            });

            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: 'e99307154c6dfb0b4750f6603256716d',
                    query: this.query
                }
            }).then((res) => {
                console.log(res.data.results)
                this.store.tvs = res.data.results
            });

        }
    }
}
</script>

<style lang="scss" scoped>
.container {
    width: 100%;
    height: 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: rgb(0, 0, 0);
}

.container> :first-child {
    color: white;
    display: flex;
    cursor: pointer;
}

ul {
    display: flex;
    align-items: center;
    gap: 40px;
    margin-left: 40px;
}

img {
    width: 100px;
}
</style>
