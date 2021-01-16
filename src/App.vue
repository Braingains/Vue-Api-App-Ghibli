<template lang='html'>
  <div class="main-container">
    <h1> Films List </h1>
    <films-filter-form :films="films" />
    <films-list :films="films"> </films-list>
    
  </div>
</template>

<script>
import { eventBus } from './main.js'
import FilmsList from './components/FilmsList.vue'
import FilmsFilterForm from './components/FilmsFilterForm.vue'

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
    'films-list': FilmsList,
    'films-filter-form' : FilmsFilterForm
    
  }
}
</script>

<style lang="css" scoped>
.main-container {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  justify-content: left;
}
</style>
