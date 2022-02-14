<template>
  <header>
    <input placeholder="Cerca qui.." type="text" v-model="query" />
    <button @click="$emit('get-api', query)">SEARCH</button>
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

<style>
</style>