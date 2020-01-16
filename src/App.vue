<template>
  <div id="app">

    <h1>BrewDog Beers</h1>
      <beers-list :beers='beers'></beers-list>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import BeerListItem from './components/BeerListItem.vue';

export default {
  name: 'app',
  data(){
    return {
      beers: []
    }
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(beers => this.beers = beers )
  },
  components: {
    "beers-list": BeersList,
    "beers-list-item": BeerListItem
  }


}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
