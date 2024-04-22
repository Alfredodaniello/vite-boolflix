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
    <div class="header p-xl-2">
        <div class="d-flex h-100 align-items-center">
            <div class="logo flex-grow-1">
                <span>Boolflix</span>
            </div>
            <div class="my-search">
                <input type="search" placeholder="Cosa vuoi Guardare?" v-model="store.search">
                <button @click="$emit('searchPerformed')">Cerca!!</button>
            </div>
    </div>

</div>

</template>

<style scoped lang="scss">
span {
            font-family: Arial, sans-serif;
            font-size: 36px;
            color: #010101;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
.header{
width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 99;
  background-color: rgb(212, 0, 0);
  height: 70px;
box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1)
}  
      
</style>