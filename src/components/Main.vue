<template>
  <main>
    <ul id="list">
      <h2>Film:</h2>
      <li v-for="film in films" :key="film.id">
        <div>Title: {{ film.title }}</div>
        <div>Original title originale: {{ film.original_title }}</div>
        <div>
          Original Language:
          <span v-if="film.original_language === 'en'"
            ><img src="../assets/img/en.png" alt="English Flag"
          /></span>
          <span v-else-if="film.original_language === 'it'"
            ><img src="../assets/img/it.png" alt="Italian Flag"
          /></span>
          <span v-else>{{ film.original_language }}</span>
        </div>
        <div>Vote Average: {{ film.vote_average }}</div>
      </li>
      <h2>TV Series:</h2>
      <li v-for="serie in tvSeries" :key="serie.id">
        <div>Title: {{ serie.name }}</div>
        <div>Original title originale: {{ serie.name }}</div>
        <div>
          Original Language:
          <span v-if="serie.original_language === 'en'"
            ><img src="../assets/img/en.png" alt="English Flag"
          /></span>
          <span v-else-if="serie.original_language === 'it'"
            ><img src="../assets/img/it.png" alt="Italian Flag"
          /></span>
          <span v-else>{{ serie.original_language }}</span>
        </div>
        <div>Vote Average: {{ serie.vote_average }}</div>
      </li>
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