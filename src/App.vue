<template>
  <div id="app">
    <h1>BrewDog Beers</h1>
      <div class="beer-container">
        <beers-list :beers='beers'></beers-list>
        <beer-detail :beer='selectedBeer'></beer-detail>
      </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import BeerListItem from './components/BeerListItem.vue';
import BeerDetail from './components/BeerDetail.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){ // Props talks to data
    return {
      beers: [],
      selectedBeer: null
    }
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(beers => this.beers = beers )

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })
  },
  components: {
    "beers-list": BeersList,
    "beers-list-item": BeerListItem,
    "beer-detail": BeerDetail
  }


}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}

.beer-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
}


#app ul {
  list-style: none;
}
</style>
