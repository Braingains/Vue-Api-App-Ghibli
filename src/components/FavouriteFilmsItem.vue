<template>
  <li v-if='film'> {{film.title}}
      <button v-on:click="removeFromFavourites"> Remove </button>
    </li>
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name: "favourite-films-item",
    props: ['film'],
    methods: {
        removeFromFavourites: function(){
            eventBus.$emit('film-to-remove', this.film)
        }
    }

}
</script>

<style>

</style>