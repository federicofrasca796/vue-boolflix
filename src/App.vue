<template>
  <div id="app">
    <site-header @input-movie="searchCallAPI" />

    <site-main :MoviesArr="this.searchedMovies" />
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
      searchedMovies: [],
    };
  },

  mounted() {},

  methods: {
    searchCallAPI(input) {
      if (input != "") {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=${this.APIkey}&language=en-US&query=${input}&page=1&include_adult=false`
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
