<template>
    <div>
    <ul>Title: {{film.title}} Year: {{film.release_date}} Reviews: {{film.rt_score}}
    </ul>
    </div>
</template>

<script>
export default {
    name: 'film-list-item',
    props: ['film'],

}
</script>

<style>

</style>