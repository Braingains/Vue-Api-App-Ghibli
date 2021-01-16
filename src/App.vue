<template>
  <div id="app">
    <films-list :films="films"> </films-list>
    <p> APP.vue test </p>
    
  </div>
</template>

<script>
import FilmsList from './components/FilmsList.vue'

export default {
  name: 'App',
  data (){
    return {
      films: [],

    }
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)


  },
  
  components: {
    'films-list': FilmsList
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
