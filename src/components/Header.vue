<template>
  <header>
    <div class="container h-100">
      <div class="d-flex justify-content-between align-items-center h-100">
        <div id="logo">
          <h1>BOOLFLIX</h1>
        </div>
        <div>
          <input
            placeholder="Cerca qui.."
            type="text"
            v-model="query"
            @keyup.enter="$emit('get-api', query)"
          />
          <button @click="$emit('get-api', query)">SEARCH</button>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      query: "",
    };
  },
  methods: {},
};
</script>

<style scoped lang="scss">
header {
  height: 100px;
  background-color: #000;
  #logo {
    color: red;
  }
}
</style>