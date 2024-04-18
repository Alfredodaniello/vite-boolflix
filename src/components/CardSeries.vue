
<script>
export default {
    name: "CardSeries",
    props: ["info"]
}
</script>

<template>
<div class="card">
  <img class="card-img-top" :src="'https://image.tmdb.org/t/p/w342' + info.poster_path" alt="Card image cap">
  <div class="card-body">
    <h4 class="card-title">{{ info.name }}</h4>
    <h5 class="card-title">{{ info.original_name }}</h5>
    <div class="img-container">
        <!--se la lingua è en stampo una bandiera inglese, altrimenti ottengo le bandiere tramite l'api gratuita-->
        <img v-if="info.original_language === 'en'" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Flag_of_England.svg/1200px-Flag_of_England.svg.png">
        <img v-else :src="'https://flagsapi.com/' + info.original_language.toUpperCase() + '/flat/64.png'" :alt=info.original_language.toUpperCase()>
    </div>
    <p>{{info.vote_average}}</p>
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
</style>