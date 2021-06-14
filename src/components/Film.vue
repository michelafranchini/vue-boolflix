<template>
    <div class="film">
        <img :src="item.poster_path" alt="">
        <h2>{{item.title}}</h2>
        <h3>Titolo originale: {{item.original_title}}</h3>
        <img class="lang" src="../assets/img/languages/en.png" alt="" v-if="item.original_language == 'en'">
        <img class="lang" src="../assets/img/languages/it.png" alt="" v-else-if="item.original_language == 'it'">
        <img class="lang" src="../assets/img/languages/all.png" alt="" v-else>
        <h4>Voto: {{item.vote_average}}</h4>
        
    </div>
</template>

<script>

export default {
    name: "Film", 
    props: ["item"], 

    computed: {
        //https://image.tmdb.org/t/p/
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    .film {
        @include starSettings;
        width: 300px;
        height: 400px;
        margin: 10px;
        padding: 10px;
        background-color: #293e6b;
        color: white;

        .lang {
            width: 30px;
        }

        h2 {
            text-align: center;
        }
    }
</style>