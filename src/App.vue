<script>
import axios from 'axios';
import { store } from './store.js';
import AppSearch from "./components/AppSearch.vue";
import Card from "./components/Card.vue";
import CardContainer from "./components/CardContainer.vue";
export default {
  name: 'App',
  components: {
    AppSearch,
    Card,
    CardContainer,
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
                query: store.search
            }
            
            let apiUrl = 'https://api.themoviedb.org/3/search/movie';
            axios.get(apiUrl, {
                params: queryParams
            })
            .then((response) => {

                    store.films = response.data.results
                    console.log(store.films)}
                    )
        }
    },
}

</script>

<template>
  <AppSearch @searchPerformed="getFilms"></AppSearch>
  <CardContainer></CardContainer>
</template>

<style>

</style>
