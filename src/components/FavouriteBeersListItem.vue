<template lang="html">


<li>{{ favouriteBeer.name }}</li>

</template>




<script>
export default {
  name: 'favourite-beer-list-item',
  props: ['favouriteBeer']

}
</script>

<style lang="css" scoped>
</style>
