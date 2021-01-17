<template>
    <div v-if='film' id='filmsDetail'>
        <div> 
                <p><span>Title</span>: {{film.title}}</p>
                <p><span>Release Date</span>: {{film.release_date}}</p>
                <p><span>Rotten Tomatoes Score</span>: {{film.rt_score}}</p>
                <p><span>Decription</span>: {{film.description}}</p>
                <button v-on:click= "addToFavourites">Add to favourites</button>
        </div>    
    </div>    
  
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'films-detail',
    props: ['film'],
    methods: {
        addToFavourites: function(){
            eventBus.$emit('film-to-save', this.film)
        }
    },
    mounted(){
        eventBus.$on('film-selected', (film) => {
            this.film = film
        })
    }

}
</script>

<style>

</style>