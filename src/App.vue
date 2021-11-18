<template>
  <div id="app">
    <input type="search" placeholder="Type a movie" v-model="inputSearch" />
    <button @click="searchCallAPI">Search</button>
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
            console.log(response.data.results);
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
</style>
