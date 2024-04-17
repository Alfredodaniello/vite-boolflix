<script>
import axios from 'axios';
import { store } from './store.js';
import AppSearch from "./components/AppSearch.vue"
export default {
  name: 'App',
  components: {
    AppSearch
  },
  data() {
        return {
            store,
        };
    },
    methods: {
        getFilms() {
            const queryParams = {
                query: store.search
            }
            
            let apiUrl = 'https://api.themoviedb.org/3/search/movie?api_key=b3e4b273d1b542085c09ffe28f143f8b';
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
</template>

<style>

</style>
