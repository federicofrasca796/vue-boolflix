<template>
  <main id="site_main">
    <div class="container">
      <div v-if="MoviesArr.length === 0">0 Movies found</div>
      <div v-else>
        <div class="movie" v-for="movie in MoviesArr" :key="movie.id">
          <h2 class="title">{{ movie.title }}</h2>
          <h3 class="og_title">{{ movie.original_title }}</h3>
          <img
            :src="require(`../assets/flags/${movie.original_language}.png`)"
            alt=""
            width="30px"
          />
          <div class="lang">{{ movie.original_language }}</div>
          <div class="rating">{{ movie.vote_average }}</div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    MoviesArr: Array,
  },
  methods: {},
};
</script>

<style lang="scss">
</style>