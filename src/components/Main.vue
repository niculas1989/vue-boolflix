<template>
  <main>
    <div id="title" v-if="!films.length && !tvSeries.length">
      <h2>CERCA FILM O SERIE TV <i class="fa-solid fa-film"></i></h2>
    </div>
    <!-- Lista in cui generare TOT elementi -->
    <div v-else class="container">
      <!-- Lista per i FILM -->
      <h2 class="text-center" v-if="films.length">Film:</h2>
      <div class="row">
        <div
          class="col col-md-6 col-lg-4 py-3"
          v-for="film in films"
          :key="film.id"
        >
          <Poster :item="film" />
        </div>
      </div>

      <!-- Lista per le SERIE TV -->
      <h2 class="text-center" v-if="tvSeries.length">TV Series:</h2>
      <div class="row">
        <div
          class="col col-md-6 col-lg-4 py-3"
          v-for="serie in tvSeries"
          :key="serie.id"
        >
          <Poster :item="serie" />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Poster from "./Poster.vue";
export default {
  name: "Main",
  components: {
    Poster,
  },
  props: ["films", "tvSeries"],
};
</script>

<style scoped lag="scss">
main {
  background-color: #676767;
  min-height: calc(100vh - 80px);
}

#title {
  min-height: calc(100vh - 80px);
  display: flex;
  justify-content: center;
  align-items: center;
}

img {
  height: 20px;
  width: 50px;
}
</style>