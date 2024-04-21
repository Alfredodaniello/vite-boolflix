<script>
import axios from 'axios';
import { store } from './store.js';
import AppSearch from "./components/AppSearch.vue";
import Card from "./components/Card.vue";
import CardContainer from "./components/CardContainer.vue";
import CardSeries from "./components/CardSeries.vue";
export default {
  name: 'App',
  components: {
    AppSearch,
    Card,
    CardContainer,
    CardSeries,
  },
  data() {
        return {
            store,
        };
    },
    methods: {
        //Funzione che effettua la chiamata all'API e aggiorna l'arrey films dentro store.js
        getFilms() {
            const queryParams = {
                //chiave necessaria fornita dall'api
                api_key: "b3e4b273d1b542085c09ffe28f143f8b",
                //QueryParams Necessaria per la corretta chiama all'api
                query: store.search,
            }
            
            let apiUrlFilms = 'https://api.themoviedb.org/3/search/movie';
            let apiUrlSeries = "https://api.themoviedb.org/3/search/tv";
            //richiesta dei film all api
            axios.get(apiUrlFilms, {
                params: queryParams
            })
            .then((response) => {

                    store.films = response.data.results
                    console.log(store.films)}
                    )
            //Richiesta delle serie all'api
            axios.get(apiUrlSeries, {
                params: queryParams
            })
            .then((response) => {

                    store.series = response.data.results
                    console.log(store.series)}
                    )
            
        }
    },
}

</script>

<template>
    <header>
        <AppSearch @searchPerformed="getFilms"></AppSearch>
    </header>
  
  <main>
    <CardContainer></CardContainer>
  </main>
  
</template>

<style>
main {
    background-color: black;
}

</style>
