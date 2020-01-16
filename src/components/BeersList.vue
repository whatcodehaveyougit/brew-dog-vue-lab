<template lang="html">
  <section>
    <ul>
      <beer-list-item v-for="(beer, index) in beers" :beer="beer" :key="index">
      </beer-list-item>
      <!-- <p>Test to show</p> -->
  </ul>
  </section>
</template>

<script>
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
