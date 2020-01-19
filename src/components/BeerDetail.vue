<template lang="html">
  <div v-if="beer" class="beer-details">
    <h3>{{ beer.name }}</h3>
    <dl>
      <dt>Tagline: {{ beer.tagline }} </dt>
      <dt>Alcohol: {{ beer.abv }}% </dt>
      <button v-on:click="addFavouriteBeer">Add to Favourite Beers!</button>
    </dl>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'beer-detail',
  props: ['beer'],
  methods: {
    addFavouriteBeer() {
      eventBus.$emit('favourite-beer', this.beer )
      // console.log(this.beer);
    }
  }
}
</script>

<style lang="css" scoped>
.beer-details {
  text-align: center;
}
</style>
