<template>
    <div>
        <ul>
            <favourite-films-item v-for="(film, index) in favouriteFilms" :film= 'film' :key= 'index'>
            </favourite-films-item>
        </ul>
    </div>
</template>

<script>
import FavouriteFilmsItem from './FavouriteFilmsItem.vue'
import { eventBus } from '../main.js'
export default {
    name: 'favourite-films',
    props: ['favouriteFilms']

,
components: {
    'favourite-films-item' : FavouriteFilmsItem
}
}
</script>

<style>

</style>