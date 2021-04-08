<template>
  <div id="app">
    <h1>Sit Back And Enjoy A Beer!</h1>
    <label for="beer_select">Select a Beer: </label>
    <select id="beer_select" v-model="selectedBeer">
      <option disabled value="">Select a beer</option>
      <option v-for="beer in beers" :key="beer.id" :value="beer">{{beer.name}}</option>
      <!-- <option v-for="beer in beers1" :key="beer.id" :value="beer">{{beer.name}}</option>
      <option v-for="beer in beers2" :key="beer.id" :value="beer">{{beer.name}}</option>
      <option v-for="beer in beers3" :key="beer.id" :value="beer">{{beer.name}}</option>
      <option v-for="beer in beers4" :key="beer.id" :value="beer">{{beer.name}}</option>
      <option v-for="beer in beers5" :key="beer.id" :value="beer">{{beer.name}}</option> -->
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
      // beers1: [],
      // beers2: [],
      // beers3: [],
      // beers4: [],
      // beers5: [],
      favouriteBeers: [],
      selectedBeer: null,
    }
  },
  components: {
    'beer-detail': BeerDetail,
    'favourite-beers': BeerFavourite
},
mounted(){
  
  // this.getBeers1(),
  // this.getBeers2(),
  // this.getBeers3(),
  // this.getBeers4(),
  // this.getBeers5(),
  this.getBeers()
  
},
methods: {
  getBeers: function() {
  fetch("https://api.punkapi.com/v2/beers?page=1&per_page=80")
  .then(res => res.json())
  .then(data => this.beers = data)
  },

  // getBeers2: function() {
  // fetch("https://api.punkapi.com/v2/beers?page=2&per_page=80")
  // .then(res => res.json())
  // .then(data => this.beers2 = data)
  // },

  // getBeers3: function() {
  // fetch("https://api.punkapi.com/v2/beers?page=3&per_page=80")
  // .then(res => res.json())
  // .then(data => this.beers3 = data)
  // },

  // getBeers4: function() {
  // fetch("https://api.punkapi.com/v2/beers?page=4&per_page=80")
  // .then(res => res.json())
  // .then(data => this.beers4 = data)
  // },

  // getBeers5: function() {
  // fetch("https://api.punkapi.com/v2/beers?page=5&per_page=80")
  // .then(res => res.json())
  // .then(data => this.beers5 = data)
  // },

  // getBeers: function(){
  // Promise.all([getBeers1(),getBeers2(),getBeers3(),getBeers4(),getbeers5()])
  // .then(res => res.json())
  // .then(data => this.beers = data)
  // },

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
