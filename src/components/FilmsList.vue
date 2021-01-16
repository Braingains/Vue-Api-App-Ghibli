<template>
    <div>
        <ul>
             <films-list-item v-for="(film, index) in films" :film='film' :key='index'> </films-list-item>
        </ul>
    </div>
</template>

<script>
import FilmsListItem from './FilmsListItem.vue';

export default {
    name: 'films-list',
    props: ['films'],

    components: { 
        "films-list-item" : FilmsListItem 
  }

}
</script>

<style>

</style>