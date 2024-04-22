<script>
export default {
    name: "Card",
    props: ["info"]
}
</script>

<template>

<div class="card mt-4">
  <img class="card-img-top" :src="'https://image.tmdb.org/t/p/w342' + info.poster_path">
  <div class="description">
    <div class="card-body">
    <div class="card-title"><span class="result">Titolo:</span> {{ info.title }}</div>
    <div class="card-title"><span class="result">Titolo originale:</span> {{ info.original_title }}</div>
    <div class="img-container d-flex align-items-center"> <span class="result">Lingua:</span> 
      <!--se la lingua è en stampo una bandiera inglese, altrimenti ottengo le bandiere tramite l'api gratuita-->
      <img class="pl-2" v-if="info.original_language === 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Flag_of_England.svg/1200px-Flag_of_England.svg.png">          
      <img class="pl-2" v-else :src="'https://flagsapi.com/' + info.original_language.toUpperCase() + '/flat/64.png'" :alt="info.original_language.toUpperCase()">
    </div>
    <!--stampo 5 stelle con un ciclo for e gli applico il colore giallo a seconda del vote.average/2-->
    <div class="d-flex vote">
      <span class="result">voto: </span>  
      <div class="rating">
        <span v-for="i in 5" :class="{ 'fas fa-star': i <= Math.floor(info.vote_average / 2), 'far fa-star': i > Math.floor(info.vote_average / 2) }"></span>
    </div>
    </div>
    <div class="mt-2"><span class="result">Overview</span>: {{ info.overview }}</div>
  </div>
  </div>
</div>
</template>

<style scoped lang="scss">
.card {
    width: calc(100% / 5 - 20px);
    height: 358.800px;
    overflow: auto;
    background-color: rgb(32, 33, 33); 
}


  .img-container {
      width: 70px;
      height: 50px;
      img {
          width: 100%;
          height: 100%;
      }
  }

.rating {
    color: #FFD700;
}

.rating .far {
    color: #ccc;
}
@media screen and (max-width: 1400px) {
    .card {
        width: calc(100% / 4 - 20px); 
    }
    .card-img-top{
      height: 100%;
    }
}
@media screen and (max-width: 1200px) {
    .card {
        width: calc(100% / 4 - 20px); 
    }
    .card-img-top{
      height: 100%;
    }
}

@media screen and (max-width: 992px) {
    .card {
        width: calc(100% / 3 - 20px); 
    }
    .card-img-top{
      height: 100%;
    }
}

@media screen and (max-width: 768px) {
    .card {
        width: calc(100% / 2 - 20px); 
    }
    .card-img-top{
      height: 100%;
    }
}

@media screen and (max-width: 576px) {
    .card {
        width: 100%; 
        margin-bottom: 20px; 
    }
    .card-img-top{
      height: 100%;
    }
}
.description {
  color: white;
  display: none;
  
}
.card:hover {
 .card-img-top {
  display: none;
 }
 .description {
  display: block;
 }
}

.result {
  color: red;
}
</style>
