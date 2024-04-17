
<script>
export default {
    name: "Card",
    props: ["info"]
}
</script>

<template>
<div class="card">
  <img class="card-img-top" src="https://img.legaseriea.it/vimages/64e37fdb/VLHDSN.png?webp&q=70&ch=840&size=454.5x-" alt="Card image cap">
  <div class="card-body">
    <h4 class="card-title">{{ info.title }}</h4>
    <h5 class="card-title">{{ info.original_title }}</h5>
    <p>{{ info.original_language }}</p>
    <p>{{info.vote_average}}</p>
  </div>
</div>
</template>

<style scoped lang="scss">
.card {
    width: calc(100% / 5 - 20px);
}
</style>