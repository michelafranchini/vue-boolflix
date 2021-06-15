<template>
    <div class="film">
        <img :src="urlImg + item.poster_path" alt="" v-if="item.poster_path">
        <img src="../assets/img/error_img.jpg" alt="" v-else >
        <div class="film_description">
            <div class="description">
                <h2>{{item.title}}</h2>
                <h2>{{item.name}}</h2>
                <h3 v-if="item.title"> {{originalTitle + item.original_title}}</h3> 
                <h3 v-else>{{originalTitle + item.original_name}}</h3>
                <img class="lang" src="../assets/img/languages/en.png" alt="" v-if="item.original_language == 'en'">
                <img class="lang" src="../assets/img/languages/it.png" alt="" v-else-if="item.original_language == 'it'">
                <img class="lang" src="../assets/img/languages/all.png" alt="" v-else>
                <h4>Voto: <span>
                    <i v-for="i in 5" :key="i" :class="i <= rating ? 'fas fa-star' : 'far fa-star'"></i>
                    </span>
                    </h4>
                <!-- <p>{{item.overview}}</p> -->
            </div>
        </div>

    </div>
</template>

<script>

export default {
    name: "Film", 
    props: ["item"],
    data() {
        return {
            urlImg: "https://image.tmdb.org/t/p/w342", 
            originalTitle: "Titolo originale: "
        }
    },
    computed: {
        rating() {
            return Math.round(Math.round(this.item.vote_average)/2)
        }
    }
    
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    .film {
        // @include starSettings;
        position: relative;
        width: 300px;
        height: 400px;
        margin: 10px;
        cursor: pointer;
        border: 3px solid #dc1a28;
        background-color: #293e6b;
        color: white;

        img {
            width: 100%;
            height: 100%;
        }

        .lang {
            width: 30px;
        }

        h2 {
            font-size: 35px;
        }
        
        h3, h4 {
            font-size: 20px;
        }
    }

    .film_description {
        visibility: hidden;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        text-align: center;
        background-color: rgba(20,44,95, 0.9);
        display: flex;
        justify-content: center;
        align-items:center; 

        .description {
            padding: 15px;
        }
    }

    .film:hover .film_description {
        visibility: visible;
    }
    
    // .fas.fa-star {
    //     width: 30px;

    // }

    .fa-star {
        color: #eda513;
        width: 30px;
        font-size: 20px;
    }
</style>