<template>
  <div>
      <Film v-for="(film, index) in films" :key="index" :item="film" />
  </div>
</template>

<script>
import axios from 'axios'; 
import Film from '../components/Film.vue'; 


export default {
    name: "Main",
    props: ["movie"], 
    components: {
        Film, 
    },
    data() {
        return {
            films: []
        }
    }, 
    created() {
        axios
            .get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: "a31b6f1e88fbabef39333e8fbdcf391b", 
                    query: "amore", 
                    language: "it-IT"
                }
            })
            .then(
                (result) => {
                    console.log(result.data);
                    this.films = result.data.results; 
                    console.log(this.films);
                }
            )
    }, 
}
</script>

<style lang="scss" scoped>

</style>