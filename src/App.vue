<template>
  <div>
    <h1>Brewdog Lab</h1>
    <beer-filter></beer-filter>
    <beer-list :listOfBeers="filtered?favouriteBeers:beers"></beer-list>
    <beer-detail :beerToDisplay="selectedBeer" :beerFavouritesList="favouriteBeers"></beer-detail>
  </div>
</template>

<script>
import BeerDetail from './components/BeerDetail.vue';
import BeerList from './components/BeerList.vue';
import BeerFilter from './components/BeerFilter.vue';
import { eventBus } from './main.js';

export default {

  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: [],
      filtered: ""
    };
  },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "beer-filter": BeerFilter
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(response => response.json())
    .then(data => this.beers = data)
    .catch(err => console.log(err))

    eventBus.$on('selected-beer', (beer) => {
      this.selectedBeer = beer
    })
    
    eventBus.$on('filter-select', (someFilterValue) => {
      this.filtered = someFilterValue
    })
  }

}

</script>

<style scoped>
  .main-container {
      display: flex;
      justify-content: space-between;
    }
</style>
