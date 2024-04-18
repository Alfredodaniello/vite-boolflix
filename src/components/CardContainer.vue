<script>
import Card from "./Card.vue";
import CardSeries from "./CardSeries.vue";
import { store } from '../store.js';
export default {
    name: "CardContainer",
    components: {
        Card,
        CardSeries
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
<div class="card-container d-flex flex-wrap">
    <!--Per ogni film ottenuto dalla chiamata all'api creo un componente Card-->
    <Card v-for="film in store.films" :info="film" :key="film.id"></Card>
    <!--Per ogni serie ottenuta dalla chiamata all'api creo un componente Card-->
    <CardSeries v-for="serie in store.series" :info="serie" :key="serie.id"></CardSeries>
</div>
</template>

<style scoped lang="scss">
.card-container {
    gap: 25px
}
</style>