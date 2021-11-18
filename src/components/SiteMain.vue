<template>
  <main id="site_main">
    <div class="container">
      <div class="movie" v-for="movie in MoviesArr" :key="movie.id">
        <h2 class="title">{{ movie.title }}</h2>
        <h3 class="og_title">{{ movie.original_title }}</h3>
        <div class="lang">{{ movie.original_language }}</div>
        <div class="rating">{{ movie.vote_average }}</div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    MoviesArr: Array,
  },
};
</script>

<style>
</style>