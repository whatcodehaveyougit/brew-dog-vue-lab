<template lang="html">
  <section>
    <li v-on:click="handleClick">{{ beer.name }}</li>
    
  </section>
</template>

<script>

import { eventBus } from '../main.js';

// export to the top of the file!
export default {
  name: 'beer-list-item',
  // Data - Props is a single beer
  props: ['beer'],
  methods: {
    // Sending beer object to App. So App to send it to Beer Detail
    handleClick() {
      eventBus.$emit('beer-selected', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>

li:hover {
  text-decoration: underline;
}
</style>
