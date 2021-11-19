<template>
  <main id="site_main">
    <div class="container">
      <div v-if="MoviesTVArr.length === 0">0 Movies found</div>
      <div v-else>
        <div
          class="movie_tv"
          v-for="movie_tv in MoviesTVArr"
          :key="movie_tv.id"
        >
          <div class="poster">
            <img
              :src="'https://image.tmdb.org/t/p/w500' + movie_tv.poster_path"
              alt=""
            />
          </div>
          <h2 class="title" v-if="movie_tv.name === undefined">
            {{ movie_tv.title }}
          </h2>
          <h2 v-else>{{ movie_tv.name }}</h2>

          <i class="og_title" v-if="movie_tv.original_name === undefined">
            {{ movie_tv.original_title }}
          </i>
          <i v-else>{{ movie_tv.original_name }}</i>

          <img
            class="lang_flag"
            :src="require(`../assets/flags/${movie_tv.original_language}.png`)"
            alt=""
            width="30px"
          />

          <div class="rating">
            {{ Math.ceil((movie_tv.vote_average * 5) / 10) }}
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    MoviesTVArr: Array,
  },
  methods: {
    convertRating() {
      this.MoviesTVArr;
    },
  },
};
</script>

<style lang="scss">
</style>