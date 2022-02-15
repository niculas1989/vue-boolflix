<template>
  <!-- Un wrapper generico in cui contenere i due componenti -->
  <div id="general-wrapper">
    <!-- Header in cui effettuare la ricerca -->
    <Header @get-api="getApi" />
    <!-- Main in cui svolgere estendere la chiamata API -->
    <Main :films="films" :tvSeries="tvSeries" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
export default {
  components: {
    Header,
    Main,
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
      if (!query) {
        this.films = [];
        this.tvSeries = [];
        return;
      }
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
