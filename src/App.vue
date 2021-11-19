<template>
  <div id="app">
    <site-header @input-movie="searchCallAPI" />

    <site-main :MoviesTVArr="this.searchedMoviesTV" />
  </div>
</template>

<script>
import axios from "axios";
import SiteHeader from "./components/SiteHeader.vue";
import SiteMain from "./components/SiteMain.vue";
export default {
  name: "App",
  components: {
    SiteHeader,
    SiteMain,
  },

  data() {
    return {
      inputSearch: "",
      APIkey: "ea6525a1837e2edd64bfb3ffbbb4b8cf",
      moviesURL: "https://api.themoviedb.org/3/search/movie?",
      tvURL: "https://api.themoviedb.org/3/search/tv?",
      searchedMoviesTV: [],
    };
  },

  mounted() {},

  methods: {
    searchCallAPI(input) {
      if (input != "") {
        axios
          .all([
            axios.get(
              `${this.moviesURL}api_key=${this.APIkey}&language=en-US&query=${input}&page=1&include_adult=false`
            ),
            axios.get(
              `${this.tvURL}api_key=${this.APIkey}&language=en-US&page=1&include_adult=false&query=${input}`
            ),
          ])
          .then(
            axios.spread((respMovies, respTV) => {
              this.searchedMoviesTV = respMovies.data.results;
              const tvShow = respTV.data.results;
              tvShow.forEach((show) => {
                this.searchedMoviesTV.push(show);
              });
              //   console.log(respTV.data.results);
              console.log(this.searchedMoviesTV);
            })
          )
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
