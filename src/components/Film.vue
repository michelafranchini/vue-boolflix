<template>
    <div class="film">
        <!-- <ul>
            <li>{{item.title}}</li>
            <li>{{item.original_title}}</li>
            <li>{{item.original_language}}</li>

        </ul> -->
        <img :src="item.poster_path" alt="">
        <h2>{{item.title}}</h2>
        <h3>{{item.original_title}}</h3>
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
        background-color: yellow;
        width: 300px;
        height: 400px;
        margin: 10px;
    }
</style>