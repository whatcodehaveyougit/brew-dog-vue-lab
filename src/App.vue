<template>
  <div id="app">
    <marquee behaviour="alternate" scrollamount="8"><h1>BrewDog Beers</h1></marquee>
      <div class="beer-container">
        <div class="col-titles">
          Brew Dog Beers List
        </div>
        <div class="col-titles">
          Selected Beer Deets
        </div>
        <div class="col-titles">
          Favourite Beerz!
        </div>
        <beers-list class="beer-col" :beers='beers'></beers-list>
        <beer-detail class="beer-col" :beer='selectedBeer'></beer-detail>
        <favourite-beers-list class="beer-col" :favouriteBeers='favouriteBeers'>
        </favourite-beers-list>
      </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import BeerListItem from './components/BeerListItem.vue';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeersList from './components/FavouriteBeersList';
import FavouriteBeersListItem from './components/FavouriteBeersListItem.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){ // Props talks to data
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    }
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(beers => this.beers = beers )

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })

    eventBus.$on('favourite-beer', (selectedBeer) => {
      this.favouriteBeers.push(selectedBeer)
    })
  },
  components: {
    "beers-list": BeersList,
    "beers-list-item": BeerListItem,
    "beer-detail": BeerDetail,
    "favourite-beers-list": FavouriteBeersList,
    "favourite-beers-list-item": FavouriteBeersListItem
  }


}

</script>

<style>

.col-titles {
  font-weight: 700;
  text-decoration: underline;
  text-align: center;
}

.beer-col {
  text-align: center;
}

h1 {
  text-align: center;
  background-color: #4CAED8;
  color: white;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}

.beer-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}


#app ul {
  list-style: none;
}
</style>
