<template>
  <div id="app">
    <Header @searchedFilm="searchItem"/>

    <main>
      <div class="film_container">
        <Film 
        :movie="newFilm" 
        v-for="(film, index) in films" 
        :key="index" 
        :item="film"/>
      </div>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'; 
import Film from './components/Film.vue'; 

import axios from 'axios'; 

export default {
  name: 'App',
  components: { 
    Header, 
    Film
  }, 
  data() {
    return {
      newFilm: "", 
      films: [],
      api_url: "https://api.themoviedb.org/3/search/movie?", 
      api_key: "api_key=a31b6f1e88fbabef39333e8fbdcf391b", 
      query: "", 
      language: ""
    }
  }, 
  methods: {
    searchItem(string) {
      this.query = string; 
          axios
          .get(`${this.api_url}${this.api_key}&query=${this.query}`)
          .then(
              (result) => {
                  console.log(result.data);
                  this.films = result.data.results; 
                  console.log(this.films);
              }
          ) 
    }, 

  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css'; 
@import './style/variables.scss';

body {
  @include starSettings;
  background-color: #131c31; 
}

main {
  height: calc(100% - 100px ) ; 
  
   .film_container {
        display: flex;
        justify-content: space-evenly;
        flex-wrap: wrap;
    }
}
</style>
