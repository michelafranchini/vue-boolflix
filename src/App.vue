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
      // api_url: "https://api.themoviedb.org/3/search/movie?", 
      // api_key: "api_key=a31b6f1e88fbabef39333e8fbdcf391b", 
      query: "", 
      language: "", 
      apiFilmUrlKey:"https://api.themoviedb.org/3/search/movie?api_key=a31b6f1e88fbabef39333e8fbdcf391b", 
      apiSeriesUrlKey: "https://api.themoviedb.org/3/search/tv?api_key=a31b6f1e88fbabef39333e8fbdcf391b"
    }
  }, 
  methods: {
    searchItem(string) {
      this.query = string; 
      const filmRequest = axios.get(`${this.apiFilmUrlKey}&query=${this.query}`); 
      const seriesRequest = axios.get(`${this.apiSeriesUrlKey}&query=${this.query}`);
      
      axios.all([filmRequest, seriesRequest])
      .then(
          axios.spread((result1, result2) => {
            this.films = result1.data.results; 
            this.films = result2.data.results;

            console.log(this.films);
          })
      );
      
    }, 

  }, 
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css'; 
@import './style/variables.scss';
@import "~@fontsource/staatliches/400.css"; 

body {
  @include starSettings;
  font-family: 'Staatliches';
  background-image: url('https://preview.redd.it/4fxxbm4opjd31.jpg?auto=webp&s=f5b7d62076600a978d290a5e87f13140c47f5cd0');
}

main {
  height: calc(100% - 100px) ;
  width: 100%;
  position: absolute;
  top: 100px;
  left: 0;
  text-align: center;
  background-color: rgba(0 ,0,0, 0.5);
  
   .film_container {
        display: flex;
        justify-content: space-evenly;
        flex-wrap: wrap;
        
    }
}
</style>
