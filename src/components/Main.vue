<template>
  <main>
    <div id="title" v-if="!films.length && !tvSeries.length">
      <h2>CERCA FILM O SERIE TV</h2>
    </div>
    <!-- Lista in cui generare TOT elementi -->
    <div v-else>
      <ul id="list">
        <!-- Lista per i FILM -->
        <div class="container">
          <h2 class="text-center" v-if="films.length">Film:</h2>
          <div class="row">
            <li v-for="film in films" :key="film.id" class="col-4 py-4">
              <div class="py-2">Title: {{ film.title }}</div>
              <div class="py-2">Original title: {{ film.original_title }}</div>
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
            <div class="py-2">Original title: {{ serie.name }}</div>
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
    </div>
  </main>
</template>

<script>
export default {
  name: "Main",
  props: ["films", "tvSeries"],
};
</script>

<style scoped lag="scss">
main {
  background-color: #676767;
  min-height: calc(100vh - 100px);
}

#title {
  min-height: calc(100vh - 100px);
  display: flex;
  justify-content: center;
  align-items: center;
}

img {
  height: 20px;
  width: 50px;
}
</style>