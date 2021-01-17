<template>
  <div class="cards">
    <div v-for="gif in gifs" :key="gif.id" class="card" style="width: 18rem;">
      <img class="card-img-top" :src="gif.images.fixed_height.url" />
      <div class="card-body">
        <h5 class="card-title">{{ gif.title }}</h5>
        <p v-if="gif.username !== ''" class="card-text">
          Usernam:{{ gif.username }}
        </p>
        <p v-else><span id="not-found" class="badge bg-danger">Username not found</span></p>
        <a :href="gif.bitly_gif_url" class="btn btn-primary">Go to GIPHY</a>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    gifs: Array,
  },
};
</script>
<style scoped>
.card {
  list-style: none;
  float: left;
  margin: 20px;
  max-width: 10000px;
  max-height: 10000px;
  border-style: solid;
  border-color:mediumpurple;
  border-width: 10px;
  border-radius: 20px;
}
.card-img-top {
  border-radius: 20px;
}
.cards {
  margin-top: 10%;
}
#not-found{
  font-size: 110%;
}
</style>
