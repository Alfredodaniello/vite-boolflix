
<script>
export default {
    name: "Card",
    props: ["info"]
}
</script>

<template>
<div class="card">
  <img class="card-img-top" :src="'https://image.tmdb.org/t/p/w342' + info.poster_path">
  <div class="card-body">
    <h4 class="card-title">{{ info.title }}</h4>
    <h5 class="card-title">{{ info.original_title }}</h5>
    <div class="img-container">
      <!--se la lingua è en stampo una bandiera inglese, altrimenti ottengo le bandiere tramite l'api gratuita-->
      <img v-if="info.original_language === 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Flag_of_England.svg/1200px-Flag_of_England.svg.png">
      <img v-else :src="'https://flagsapi.com/' + info.original_language.toUpperCase() + '/flat/64.png'" :alt=info.original_language.toUpperCase()>
    </div>
    <p>{{ Math.floor(info.vote_average / 2) }}</p>
    <!--stampo 5 stelle con un ciclo for e gli applico il colore giallo a seconda del vote.average/2-->
    <div class="rating">
        <span v-for="i in 5" :class="{ 'fas fa-star': i <= Math.floor(info.vote_average / 2), 'far fa-star': i > Math.floor(info.vote_average / 2) }"></span>
      </div>
  </div>
</div>
</template>

<style scoped lang="scss">
.card {
    width: calc(100% / 5 - 20px);
}
.img-container {
  width: 50px;
  height: 75px;
  img{
    width: 100%;
  }

}
.rating {
  color: #FFD700; 
}
.rating .far {
  color: #ccc; 
}
</style>