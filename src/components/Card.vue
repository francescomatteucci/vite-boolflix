<template>
    <div class="card" @mouseenter="showInfo" @mouseleave="hideInfo">
        <li>
            <div class="image-container">
                <img v-if="item.poster_path === null" src="../assets/Nofound.png" alt="">
                <img v-else :src="imageCheck()">
            </div>
            <div class="info-container" v-show="showDetails">
                <p v-if="item.original_title"> Nome Film originale: {{ item.original_title }}</p>
                <p v-if="item.original_name">Nome Serie originale: {{ item.original_name }}</p>
                <p v-html="fetchFlag()"></p>
                <p>
                    <font-awesome-icon v-for="index in 5" :key="index"
                        :icon="[index <= averageVote() ? 'fas' : 'far', 'star']" />
                </p>
                <p>{{ item.overview }}</p>
            </div>
        </li>
    </div>
</template>



<script>

export default {
    props: {
        item: {
            type: Object,
            required: true,
        },

    },
    data() {
        return {
            showDetails: false,
        };
    },
    methods: {
        fetchFlag() {
            if (this.item.original_language === 'it') {
                return `<div><img src="Flag_of_Italy.svg.png" alt=""></div>`
            } else if (this.item.original_language === 'en') {
                return `<div><img src="/download.png" alt=""></div>`
            }
            else if (this.item.original_language === 'sv') {
                return `<div><img src="Flag_of_Slovenia.svg.png" alt=""></div>`
            }
            else {
                return this.item.original_language
            }

        },
        imageCheck() {
            return `http://image.tmdb.org/t/p/w342/${this.item.poster_path}`
        },
        averageVote() {
            return Math.round(this.item.vote_average / 2);
        },
        showInfo() {
            this.showDetails = true;
        },
        hideInfo() {
            this.showDetails = false;
        },
    }
}
</script>

<style lang="scss" scoped>
p > * {
    color: yellow;
}

img {
    width: 100%;
    aspect-ratio: 4/6;
}

.card {
    width: 200px;
    display: flex;
    border: 1px solid black;
}

.image-container {
  position: relative;
}

.image-container:hover img {
  opacity: 0.7;
}

.info-container {
  position: absolute;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.7);
  color: white;
  padding: 10px;
  display: none;
}

.card:hover .info-container {
  display: block;
}
</style>