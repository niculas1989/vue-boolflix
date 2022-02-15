<template>
  <ul>
    <div>
      <figure>
        <img :src="images" :alt="item.title" class="h-100 w-100" />
      </figure>
    </div>

    <div class="h-100 w-100 justify-content-center align-items-center">
      <li>{{ item.title || item.name }}</li>
      <li>{{ item.original_title || item.original_name }}</li>
      <li>
        <img v-if="hasFlags" :src="flagSrc" alt="Language Flag" class="w-75" />
        <span v-else>{{ item.original_language }}</span>
      </li>
      <li>
        <i
          v-for="(star, index) in stars"
          :key="index"
          class="fa-solid fa-star"
        ></i>
        <i
          v-for="(empyStar, index) in restOfStars"
          :key="index"
          class="fa-regular fa-star"
        ></i>
      </li>
    </div>
  </ul>
</template>

<script>
export default {
  name: "Poster",
  props: ["item"],
  data() {
    return {
      flags: ["it", "en"],
      hover: "false",
    };
  },
  computed: {
    images() {
      if (!this.item.poster_path) {
        return "https://media.istockphoto.com/photos/computer-error-picture-id1222806141?k=20&m=1222806141&s=612x612&w=0&h=GoODCHnR0mSefDBLWJpnqVnfRKH9ttdYPO0-KEYbb7w=";
      } else {
        return `https://image.tmdb.org/t/p/w342/${this.item.poster_path}`;
      }
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
    restOfStars() {
      return 5 - this.stars;
    },
  },
};
</script>

<style scoped lang="scss">
ul li {
  list-style-type: none;
}

.active {
  background-color: #000;
  height: 100%;
}
</style>