<template>
  <div>
    <input type="text" v-model="query" />
    <button @click="getApi">CLICCAMI</button>
    <ul id="list">
      <li v-for="(film, index) in films" :key="index">
        <div>Title: {{ film.title }}</div>
        <div>Original title originale: {{ film.original_title }}</div>
        <div>
          Original Language:
          <span v-if="(original_language = 'en')"
            ><img src="./assets/img/en.png" alt="English Flag"
          /></span>
          <span v-else-if="(original_language = 'it')"
            ><img src="./assets/img/it.png" alt="Italian Flag"
          /></span>
          <span v-else>{{ film.original_language }}</span>
        </div>
        <div>Vote Average: {{ film.vote_average }}</div>
      </li>
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
      query: "",
      english: "@assets/img/en.png",
      italian: "@assets/img/it.png",
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
        });
    },
  },
};
</script>

<style lang="scss">
</style>
