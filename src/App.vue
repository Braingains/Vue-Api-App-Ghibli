<template lang='html'>
  <div class="main-container">
    <h1> Films List </h1>
    <films-filter-form :films="films" /> </films-filter-form>
    <!-- <films-list :films="films"> </films-list> -->
    <films-detail :films="films"> </films-detail>
    <favourite-films :favouriteFilms='favourites'> </favourite-films>
    
  </div>
</template>

<script>
import { eventBus } from './main.js'
import FilmsList from './components/FilmsList.vue'
import FilmsFilterForm from './components/FilmsFilterForm.vue'
import FilmsDetail from './components/FilmsDetail.vue'
import FavouriteFilms from './components/FavouriteFilms.vue'

export default {
  name: 'App',
  data (){
    return {
      films: [],
      favourites:[],
      selectedFilm: null,
      filmToSave: null


    }
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)
    

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })

    eventBus.$on('film-to-save', (film) => {
      if(!this.favourites.include(film)){
        this.favourites.push(film)
      }
    })


  },
  
  components: {
    'films-list': FilmsList,
    'films-filter-form' : FilmsFilterForm,
    'films-detail' : FilmsDetail,
    'favourite-films': FavouriteFilms
    
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
