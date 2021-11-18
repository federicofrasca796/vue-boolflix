<template>
  <header id="site_header">
    <input type="search" placeholder="Type a movie" v-model="inputSearch" />
    <button @click="$emit('input-movie', inputSearch)">Search</button>
  </header>
</template>

<script>
export default {
  data() {
    return {
      inputSearch: "",
    };
  },
  methods: {},
};
</script>

<style>
</style>