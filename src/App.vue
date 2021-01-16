<template>
  <div id="app">
    <p> APP.vue test </p>
  </div>
</template>

<script>


export default {
  name: 'App',
  data (){
    return {
      beers: [],

    }
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(beers => this.beers = beers);
  },
  components: {
    
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
