<script>
import Card from "./Card.vue";
import { store } from '../store.js';
export default {
    name: "CardContainer",
    components: {
        Card
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
</div>
</template>

<style scoped lang="scss">
.card-container {
    gap: 25px
}
</style>