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
    <div class="container">
      <div class="card-container d-flex flex-wrap justify-content-center">
        <!--Per ogni film ottenuto dalla chiamata all'api creo un componente Card-->
        <Card v-for="film in store.films" :info="film" :key="film.id"></Card>
        <!--Per ogni serie ottenuta dalla chiamata all'api creo un componente Card-->
        <CardSeries v-for="serie in store.series" :info="serie" :key="serie.id"></CardSeries>
      </div>
    </div>
  </template>
  
  <style scoped lang="scss">
  .card-container {
    margin: auto; 
    gap: 25px; 
  }

  .container {
    padding-top: 100px;
    padding-bottom: 20px;
  }
  </style>
  