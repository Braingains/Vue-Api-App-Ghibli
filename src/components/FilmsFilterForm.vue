<template>
  <form v-on:submit.prevent>
    <input type="text" v-model="search" placeholder="search for movie" v-on:keyup="searchForFilm">
    <select v-on:change="handleSelect" v-model="selectedFilm">
      <option disabled value="">Select a Movie..</option>
      <option v-for="(film, index) in films" :value="film" :key="index">{{film.title}}</option>
    </select>
  </form>
</template>

<script>
import { eventBus } from '../main'
export default {
    name: "films-filter-form",
    data(){
        return {
            'search': "",
            'selectedFilm': {}
        }
    },
    props: ["films"],
    methods: {
        searchForFilm(){
            let foundFilm = this.films.find((film) => {
                return film.title.toLowerCase().indexOf(this.search.toLowerCase()) > -1
            })
            this.selectedFilm = foundFilm

            eventBus.$emit('film-selected', this.selectedFilm)
        },
        handleSelect(){
            this.search = ""
            eventBus.$emit('film-selected', this.selectedFilm)
        }
    }

}
</script>

<style>

</style>