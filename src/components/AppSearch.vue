<script>
import { store } from '../store.js';
import axios from 'axios';
export default {
    name: "AppSearch",
    data() {
        return {
            store,
        };
    }
}
    

</script>

<template>

<input type="search" v-model="store.search">
<button @click="$emit('searchPerformed')">Cerca!</button>
</template>

<style scoped lang="scss">

</style>