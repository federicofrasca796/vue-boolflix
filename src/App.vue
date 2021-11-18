<template>
  <div id="app">
    <input type="search" placeholder="Type a movie" v-model="inputSearch" />
    <button @click="searchCallAPI">Search</button>

    <div class="container">
      <div class="movie" v-for="movie in searchedMovies" :key="movie.id">
        <h2 class="title">{{ movie.title }}</h2>
        <h3 class="og_title">{{ movie.original_title }}</h3>
        <div class="lang">{{ movie.original_language }}</div>
        <div class="rating">{{ movie.vote_average }}</div>
      </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from "axios";

export default {
  name: "App",
  components: {},

  data() {
    return {
      inputSearch: "",
      searchedMovies: [],
    };
  },

  mounted() {},

  methods: {
    searchCallAPI() {
      if (this.inputSearch != "") {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=ea6525a1837e2edd64bfb3ffbbb4b8cf&language=en-US&query=${this.inputSearch}&page=1&include_adult=false`
          )
          .then((response) => {
            this.searchedMovies = response.data.results;
            console.log(this.searchedMovies);
          })
          .catch((error) => {
            console.log("API ERROR:" + error);
          });
      }
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/variables.scss";
@import "./assets/scss/common.scss";

.movie {
  margin: 2rem 0;
}
</style>
