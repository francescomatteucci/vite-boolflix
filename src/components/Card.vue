<template>
    <li>
        <p>{{ item.title }}</p>
        <img :src="imageCheck()" alt="">
        <p>{{ item.name }}</p>
        <p>{{ item.original_title }}</p>
        <p>{{ item.original_name }}</p>
        <p v-html="fetchFlag()"></p>
        <p v-if="item.vote_average >= 2">
            <font-awesome-icon v-for="index in 5" :key="index" :icon="[index <= averageVote() ? 'fas' : 'far', 'star']" />
        </p>
    </li>
</template>

<script>

export default {
    props: {
        item: {
            type: Object,
            required: true,
        },
        
    },
    methods:{
        fetchFlag(){
            if(this.item.original_language === 'it'){
                return `<div><img src="public/Flag_of_Italy.svg.png" alt=""></div>`
            }else if(this.item.original_language === 'en'){
                return `<div><img src="public/download.png" alt=""></div>`
            }
            else if(this.item.original_language === 'sv'){
                return `<div><img src="public/Flag_of_Slovenia.svg.png" alt=""></div>`
            }
             else{
                return this.item.original_language
            }
  
        },
        imageCheck(){
            return `http://image.tmdb.org/t/p/w500/${this.item.backdrop_path}`
        },
        averageVote() {
            return Math.round(this.item.vote_average / 2);
        }
    }
}
</script>

<style lang="scss" scoped></style>