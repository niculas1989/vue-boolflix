<template>
  <div>
    <input type="text" v-model="query" />
    <button @click="getApi">CLICCAMI</button>
    <ul id="list">
      <li>QUALCOSA ANDRA' QUI</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      films: [],
      api_key: "90fa42f2bc227218b6f76248ac1d9928",
      uri: "https://api.themoviedb.org/3/",
      query: "",
    };
  },
  methods: {
    getApi() {
      const config = {
        params: {
          api_key: this.api_key,
          query: this.query,
          language: "it-IT",
        },
      };

      axios
        .get("https://api.themoviedb.org/3/search/movie", config)
        .then((res) => {
          this.films = res.data.results;
          console.log(this.films);
        });
    },
  },
};
</script>

<style lang="scss">
</style>
