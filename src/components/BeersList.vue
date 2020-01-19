<template lang="html">

    <section class="beer-section">
      <ul>
        <beer-list-item v-for="(beer, index) in beers" :beer="beer" :key="index">
        </beer-list-item>
        <!-- <p>Test to show</p> -->
      </ul>
    </section>
</template>

<script>
// Ul can't exist without <li> so here we are bringing in the list items
import BeerListItem from './BeerListItem.vue';

// Here we are getting passed down the beers array of objects
// components register to pass to html template
export default {
  name: 'beers-list',
  props: ['beers'],
    components: {
      "beer-list-item": BeerListItem
    }
}
</script>

<style lang="css" scoped>
</style>
