<template>

    <div id="selected_beer">
    <h2> {{selectedBeer.name}} </h2>
        <p> Tagline: {{selectedBeer.tagline}} </p>
        <p> Description: {{selectedBeer.description}} </p>
        <img class="imgBeer" :src="selectedBeer.image_url" alt="beerPic">
        <section class="ing">
            <div>
                <h2> Malt Ingredients </h2>
                <p v-for="malt in selectedBeer.ingredients.malt">{{malt.name}}</p>
            </div>
            <div>
                <h2> Hops Ingredients </h2>
                <p v-for="hops in selectedBeer.ingredients.hops">{{hops.name}}</p>
            </div>
            <div>
                <h2> Yeast Ingredients </h2>
                <p>{{selectedBeer.ingredients.yeast}}</p>
            </div>
            <div>
                <h2> Food Pairings </h2>
                <p v-for="food in selectedBeer.food_pairing">{{food}}</p>
            </div>
        </section>
        
    </div>

</template>

<script>
export default {
    name: "beer-detail",
    props: ["selectedBeer"],
    methods: {
        uniqueBeer: function () {
            return unique = [...new Set ([ingredients])];
        }
    }
}
</script>

<style>
.imgBeer {
    height: 150px;
}
.ing {
    display: flex;
    text-align: center;
    margin: 10px;
}
h2 {
    margin: 20px;
}
</style>