<template lang="html">
  <div id="favourite_beers">
    <h2>Favourite Beers</h2>
    <ul>
      <li v-for="favouriteBeer in favouriteBeers">{{favouriteBeer.name}} <img class="small-beer" :src="favouriteBeer.image_url"/><br><button @click="removeFromFavourites(favouriteBeer)"> Remove Beer</button>
</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'favourite-beers',
  props: ['favouriteBeers'],
  methods:{
    removeFromFavourites: function(Beer) {
    this.favouriteBeers.pop(Beer)
  }
  }
}
</script>

<style lang="css" scoped>
.small-beer {
  height: 50px;
}

li {
    list-style: none;
}

</style>
