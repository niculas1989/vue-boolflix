<template>
  <li>
    <strong>Cast: </strong>
    <em v-for="(i, index) in item" :key="index" class="d-flex flex-column"
      ><span v-if="index < 5">{{ i.name }}</span></em
    >
  </li>
</template>

<script>
export default {
  name: "Cast",
  props: ["item"],
};
</script>

<style>
</style>