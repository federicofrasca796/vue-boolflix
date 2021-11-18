<template>
  <div id="app">
    <input type="search" placeholder="Type a movie" v-model="inputSearch" />
    <button>Search</button>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import axios from "axios";
export default {
  name: "App",
  components: {},
  data() {
    return {
      inputSearch: "",
    };
  },
};
</script>

<style lang="scss">
@import "./assets/scss/variables.scss";
@import "./assets/scss/common.scss";
</style>
