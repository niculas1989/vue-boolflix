<template>
  <ul class="card-wrapper">
    <img
      id="posters"
      :src="images"
      :alt="item.title"
      @mouseenter="hover = true"
    />

    <div class="hover-option py-3" @mouseleave="hover = false" v-if="hover">
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
      <Cast :item="castList" />
    </div>
  </ul>
</template>

<script>
import axios from "axios";
import Cast from "./Cast.vue";

export default {
  name: "Poster",
  props: ["item"],
  components: {
    Cast,
  },
  data() {
    return {
      flags: ["it", "en"],
      hover: false,
      totalStars: 5,
      castList: [],
      apiCast: {
        api_key: "90fa42f2bc227218b6f76248ac1d9928",
        baseUri: "https://api.themoviedb.org/3/movie/",
        endUri: "/credits",
      },
    };
  },
  methods: {
    fetchApiCredits() {
      if (this.item) {
        const { api_key, baseUri, endUri } = this.apiCast;
        const config = {
          params: {
            api_key,
            language: "it-IT",
          },
        };

        axios.get(baseUri + this.item.id + endUri, config).then((res) => {
          this.castList = res.data.cast;
        });
      }
    },
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
  mounted() {
    this.fetchApiCredits();
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
  height: 513px;
  width: 342px;
}
#posters {
  height: 513px;
  width: 342px;
  border: 1px solid red;
  border-radius: 30px;
  box-shadow: 0px 0px 10px 2px #d80909;
}
.hover-option {
  position: absolute;
  z-index: 1;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  background-color: #000;
  border-radius: 30px;
  height: 513px;
  width: 342px;
  overflow-y: auto;
  transform: translateX(10%);
}
</style>