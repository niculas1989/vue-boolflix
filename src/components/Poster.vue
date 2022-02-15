<template>
  <ul>
    <li>{{ item.title || item.name }}</li>
    <li>{{ item.original_title || item.original_name }}</li>
    <li>
      <img v-if="hasFlags" :src="flagSrc" alt="Language Flag" class="w-75" />
      <span v-else>{{ item.original_language }}</span>
    </li>
    <li>{{ stars }}</li>
    <i class="fa-solid fa-star"></i>
    <li>
      <figure>
        <img :src="images" :alt="item.title" class="h-100 w-100" />
      </figure>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Poster",
  props: ["item"],
  data() {
    return {
      flags: ["it", "en"],
    };
  },
  computed: {
    images() {
      return `https://image.tmdb.org/t/p/w342/${this.item.poster_path}`;
    },
    flagSrc() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
    hasFlags() {
      return this.flags.includes(this.item.original_language);
    },
    stars() {
      return Math.ceil(this.item.vote_average / 2);
    },
  },
};
</script>

<style scoped lang="scss">
ul li {
  list-style-type: none;
}
</style>