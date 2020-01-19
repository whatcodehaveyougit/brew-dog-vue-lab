<template lang="html">

  <section class="favourite-beers-section">
    <ul>
      <favourite-beers-list-item  v-for="(favouriteBeer, index) in favouriteBeers" :favouriteBeer="favouriteBeer" :key="index">

      </favourite-beers-list-item>
      <!-- <p>Test to show</p> -->
    </ul>
  </section>
</template>

<script>
import FavouriteBeersListItem from './FavouriteBeersListItem.vue'

export default {
  name: "favourite-beers",
  props: ['favouriteBeers'],
  components: {
    "favourite-beers-list-item": FavouriteBeersListItem
  }
}
</script>

<style lang="css" scoped>
</style>
