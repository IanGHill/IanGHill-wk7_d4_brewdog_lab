<template>
  <div>
      <ul>
          <list-item v-for="beer in listOfBeers" :indivBeer="beer" :key="beer.id"></list-item>
      </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'beer-list',
  props: ['listOfBeers'],
  components: {
    'list-item': ListItem  
  }
}
</script>

<style scoped>
  
</style>