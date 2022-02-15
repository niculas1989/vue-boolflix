<template>
  <ul class="card-wrapper">
    <img
      id="posters"
      :src="images"
      :alt="item.title"
      @mouseenter="hover = true"
    />

    <div class="hover-option" @mouseleave="hover = false" v-if="hover">
      <li>{{ item.title || item.name }}</li>
      <li>{{ item.original_title || item.original_name }}</li>
      <li>
        <img v-if="hasFlags" :src="flagSrc" alt="Language Flag" class="flags" />
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
      <li>
        <p>
          <strong>Trama: </strong
          ><em> {{ item.overview || "Non Disponibile" }}</em>
        </p>
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
      hover: false,
      totalStars: 5,
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
      return this.totalStars - this.stars;
    },
  },
};
</script>

<style scoped lang="scss">
.flags {
  height: 25px;
  width: 40px;
}

li {
  list-style-type: none;
  color: white;
}

i {
  color: #ffbd00;
}

.card-wrapper {
  position: relative;
  #posters {
    height: 513px;
    width: 342px;
    border: 1px solid black;
    border-radius: 30px;
    box-shadow: 0px 0px 10px 2px #000000;
  }
  .hover-option {
    position: absolute;
    z-index: 2;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: rgba(#000, 0.9);
    border-radius: 30px;
    height: 513px;
    width: 342px;
    overflow-y: auto;
  }
}
</style>