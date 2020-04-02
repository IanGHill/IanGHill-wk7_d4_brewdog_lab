<template>
  <div v-if="beerToDisplay">
    <h3>Beer Details</h3>
    <button v-on:click="addToFavourites()">Add to Favourites</button>

    <p>{{beerToDisplay.name}}</p>
    <p>{{beerToDisplay.tagline}}</p>
    <p>ABV: {{beerToDisplay.abv}}</p>
    <p>{{beerToDisplay.description}}</p>
    <p>IBU: {{beerToDisplay.ibu}}</p>
    <p>{{favouritesCheck()?'Favourited':''}}</p>
    <img :src='beerToDisplay.image_url' alt="beer-img">
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
    name: 'beer-detail',
    props: ['beerToDisplay', 'beerFavouritesList'],
    methods: {
      favouritesCheck: function () {
        return this.beerFavouritesList.includes(this.beerToDisplay);
      },
      addToFavourites: function () {
        this.beerFavouritesList.push(this.beerToDisplay);
      }
    }
}
</script>

<style scoped>
  p {
    color: red;
  }
</style>