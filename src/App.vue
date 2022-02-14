<template>
  <div id="general-wrapper">
    <Header @get-api="getApi" />
    <main>
      <ul id="list">
        <h2>Film:</h2>
        <li v-for="film in films" :key="film.id">
          <div>Title: {{ film.title }}</div>
          <div>Original title originale: {{ film.original_title }}</div>
          <div>
            Original Language:
            <span v-if="film.original_language === 'en'"
              ><img src="./assets/img/en.png" alt="English Flag"
            /></span>
            <span v-else-if="film.original_language === 'it'"
              ><img src="./assets/img/it.png" alt="Italian Flag"
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
              ><img src="./assets/img/en.png" alt="English Flag"
            /></span>
            <span v-else-if="serie.original_language === 'it'"
              ><img src="./assets/img/it.png" alt="Italian Flag"
            /></span>
            <span v-else>{{ serie.original_language }}</span>
          </div>
          <div>Vote Average: {{ serie.vote_average }}</div>
        </li>
      </ul>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
export default {
  components: {
    Header,
  },
  data() {
    return {
      films: [],
      tvSeries: [],
      api_key: "90fa42f2bc227218b6f76248ac1d9928",
    };
  },
  methods: {
    getApi(query) {
      const config = {
        params: {
          api_key: this.api_key,
          query: query,
          language: "it-IT",
        },
      };

      axios
        .get("https://api.themoviedb.org/3/search/movie", config)
        .then((res) => {
          this.films = res.data.results;
        });

      axios
        .get("https://api.themoviedb.org/3/search/tv", config)
        .then((res) => {
          this.tvSeries = res.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
