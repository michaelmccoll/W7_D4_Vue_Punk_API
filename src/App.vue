<template>
  <div id="app">
    <h1>hello</h1>
    <label for="beer_select">Select a Beer:</label>
    <select id="beer_select" v-model="selectedBeer">
      <option disabled value="">Select a beer</option>
      <option v-for="beer in beers" :key="beer.id" :value="beer">{{beer.name}}</option>
    </select>

    <beer-detail v-if="selectedBeer" :selectedBeer="selectedBeer"></beer-detail>

    <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addToFavourites">Add Beer</button>

    <favourite-beers :favouriteBeers="favouriteBeers"></favourite-beers>

  </div>
</template>

<script>
import BeerDetail from './components/BeerDetail.vue';
import BeerFavourite from './components/BeerFavourite';

export default {
  name: 'App',
  data(){
    return {
      beers: [],
      favouriteBeers: [],
      selectedBeer: null,
    }
  },
  components: {
    'beer-detail': BeerDetail,
    'favourite-beers': BeerFavourite
},
mounted(){
  this.getBeers()
},
methods: {
  getBeers: function() {
  fetch("https://api.punkapi.com/v2/beers?page=1&per_page=80")
  .then(res => res.json())
  .then(data => this.beers = data)
  },
  addToFavourites: function() {
    this.favouriteBeers.push(this.selectedBeer)
  },
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
