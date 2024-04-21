
<script>
export default {
    name: "CardSeries",
    props: ["info"]
}
</script>

<template>
<div class="card">
  <img class="card-img-top" :src="'https://image.tmdb.org/t/p/w342' + info.poster_path" alt="Card image cap">
  <div class="description">
    <div class="card-body">
    <h4 class="card-title">{{ info.name }}</h4>
    <h5 class="card-title">{{ info.original_name }}</h5>
    <div class="img-container">
        <!--se la lingua è en stampo una bandiera inglese, altrimenti ottengo le bandiere tramite l'api gratuita-->
        <img v-if="info.original_language === 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Flag_of_England.svg/1200px-Flag_of_England.svg.png">
        <img v-else :src="'https://flagsapi.com/' + info.original_language.toUpperCase() + '/flat/64.png'" :alt=info.original_language.toUpperCase()>
    </div>
    <p>{{ Math.floor(info.vote_average / 2) }}</p>
    <div class="rating">
        <span v-for="i in 5" :class="{ 'fas fa-star': i <= Math.floor(info.vote_average / 2), 'far fa-star': i > Math.floor(info.vote_average / 2) }"></span>
      </div>
  </div>
  </div>
</div>
</template>

<style scoped lang="scss">
.card {
    width: calc(100% / 5 - 20px);
    border: red; 
}


.img-container {
    width: 50px;
    height: 75px;
    img {
        width: 100%;
    }
}

.rating {
    color: #FFD700;
}

.rating .far {
    color: #ccc;
}
.description {
  color: white;
  min-height: 358.800px;
  display: none;
  background-color: rgba(0, 0, 0, 0.9);; 
}
.card:hover {
 .card-img-top {
  display: none;
 }
 .description {
  display: block;
 }
}

@media screen and (max-width: 1200px) {
    .card {
        width: calc(100% / 4 - 20px); 
    }
}

@media screen and (max-width: 992px) {
    .card {
        width: calc(100% / 3 - 20px); 
    }
}

@media screen and (max-width: 768px) {
    .card {
        width: calc(100% / 2 - 20px); 
    }
}

@media screen and (max-width: 576px) {
    .card {
        width: 100%; 
        margin-bottom: 20px; 
    }
}

</style>
