<template>
  <div>
    <input type="text" />
    <button>CLICCAMI</button>
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
      qualcosaVaQui: "",
    };
  },
  methods: {
    getApi() {
      axios.get("URLVAQUI").then((res) => {
        //!QUI FAREMO QUALCOSA
      });
    },
  },
};
</script>

<style lang="scss">
</style>
