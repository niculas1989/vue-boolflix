<template>
  <main>
    <!-- Lista in cui generare TOT elementi -->
    <ul id="list">
      <!-- Lista per i FILM -->

      <div class="container">
        <h2 class="text-center" v-if="films.length">Film:</h2>
        <div class="row">
          <li v-for="film in films" :key="film.id" class="col-4 py-4">
            <div class="py-2">Title: {{ film.title }}</div>
            <div class="py-2">
              Original title originale: {{ film.original_title }}
            </div>
            <div>
              Original Language:
              <span class="py-2" v-if="film.original_language === 'en'"
                ><img src="../assets/img/en.png" alt="English Flag"
              /></span>
              <span class="py-2" v-else-if="film.original_language === 'it'"
                ><img src="../assets/img/it.png" alt="Italian Flag"
              /></span>
              <span class="py-2" v-else>{{ film.original_language }}</span>
            </div>
            <div class="py-2">Vote Average: {{ film.vote_average }}</div>
          </li>
        </div>
      </div>

      <!-- Lista per le SERIE TV -->

      <h2 class="text-center" v-if="tvSeries.length">TV Series:</h2>
      <div class="row">
        <li v-for="serie in tvSeries" :key="serie.id" class="col-4 py-4">
          <div class="py-2">Title: {{ serie.name }}</div>
          <div class="py-2">Original title originale: {{ serie.name }}</div>
          <div>
            Original Language:
            <span class="py-2" v-if="serie.original_language === 'en'"
              ><img src="../assets/img/en.png" alt="English Flag"
            /></span>
            <span class="py-2" v-else-if="serie.original_language === 'it'"
              ><img src="../assets/img/it.png" alt="Italian Flag"
            /></span>
            <span class="py-2" v-else>{{ serie.original_language }}</span>
          </div>
          <div class="py-2">Vote Average: {{ serie.vote_average }}</div>
        </li>
      </div>
    </ul>
  </main>
</template>

<script>
export default {
  name: "Main",
  props: ["films", "tvSeries"],
};
</script>

<style scoped>
img {
  height: 20px;
  width: 50px;
}
</style>