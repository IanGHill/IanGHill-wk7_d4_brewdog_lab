<template>
  <div>
    <li v-on:click="handleClick">{{indivBeer.name}}</li>
  </div>
</template>

<script>
import {eventBus} from '../main.js';
export default {
    name: 'list-item',
    props: ['indivBeer'],
    methods: {
        handleClick(){
            eventBus.$emit('selected-beer', this.indivBeer)
        }
    }

}
</script>

<style scoped>

</style>