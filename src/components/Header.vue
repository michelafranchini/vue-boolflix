<template>
  <header>
        <div class="header_container">
            <img src="../assets/img/logo.png" alt="logo">
            <div>
                <input type="text" 
                placeholder="Cosa vuoi guardare?"
                v-model.trim="filmSearched"
                @keyup="$emit('searchedFilm', filmSearched)">
                <button @click="$emit('searchedFilm', filmSearched)">Cerca</button>
            </div>
        </div>
  </header>
</template>

<script>
export default {
    name: "Header",

    data() {
        return{
            filmSearched: ""
        }
    }
} 

</script>

<style lang="scss" scoped>
@import '../style/variables.scss';
@import "~@fontsource/staatliches/400.css";

    .header_container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 30px;
        height: 100px;
        background-color: #293e6b;

        input {
            width: 400px;
            height: 30px;
            padding:  0 10px;
            border: 2px solid #dc1a28;
            border-radius: 7px;
            font-size: 20px;
            font-family: 'Staatliches';
            color: black;
        }

        button {
            height: 30px;
            width: 80px;
            margin-left: 20px;
            font-size: 18px;
            font-family: 'Staatliches';
            background-color: #dc1a28;
            color: white ;
        }
    }
</style>