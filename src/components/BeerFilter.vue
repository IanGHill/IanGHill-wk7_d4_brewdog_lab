<template>
  <div>
    <form>
      <label for="unfilter">All Beers</label>
      <input type="radio" name="filtering-beers" value="" checked="checked" v-model="filtering">
      <label for="filter">Favourites</label>
      <input type="radio" name="filtering-beers" value="FILTER" v-model="filtering">
    </form>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  data() {
    return {
      filtering: ""
    }
  },
  name: 'beer-filter',
  watch: {
    filtering: function (newFilter, oldFilter) {
      eventBus.$emit('filter-select', this.filtering) 
    }
  }
}
</script>

<style scoped>

</style>