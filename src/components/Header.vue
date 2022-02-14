<template>
  <header>
    <input type="text" v-model="query" />
    <button @click="$emit('get-api', query)">CLICCAMI</button>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: ["query"],
  methods: {
    newValue(changedValue) {
      this.query = changedValue;
      this.$emit(this.newValue, changedValue);
    },
  },
};
</script>

<style>
</style>