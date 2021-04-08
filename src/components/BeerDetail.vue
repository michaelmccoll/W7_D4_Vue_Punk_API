<template>

    <div id="selected_beer">
    <h2> {{selectedBeer.name}} </h2>
    <p> Tagline: {{selectedBeer.tagline}} </p>
    <img class="imgBeer" :src="selectedBeer.image_url" alt="beerPic">
    </div>

</template>

<script>
export default {
    name: "beer-detail",
    props: ["selectedBeer"],

}
</script>

<style>
.imgBeer {
    height: 100px;
}
</style>