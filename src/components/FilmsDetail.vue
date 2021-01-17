<template>
    <div v-if='film' id='filmDetail'>
        <div> 
                <p><span>Title</span>: {{film.title}}</p>
                <p><span>Release Date</span>: {{film.release_date}}</p>
                <p><span>Rotten Tomatoes Score</span>: {{film.rt_score}}</p>
        </div>    
    </div>    
  
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'film-detail',
    data(){
        return {
            film: null
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