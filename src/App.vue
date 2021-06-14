<template>
  <div id="app">
    <Header @searchedFilm="searchItem"/>

    <main>
      <Main :movie="newFilm"/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: { 
    Header, 
    Main
  }, 
  data() {
    return {
      newFilm: ""
    }
  }, 
  methods: {
    searchItem(string) {
      this.newFilm = string
    }
  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css'; 
@import './style/variables.scss';

body {
  @include starSettings; 
}

main {
  height: calc(100vh - 100px ) ; 
  background-color: #3170cf;

}
</style>
