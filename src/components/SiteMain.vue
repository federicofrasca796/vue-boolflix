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
          <div class="poster" v-if="movie_tv.poster_path != null">
            <img
              :src="'https://image.tmdb.org/t/p/w500' + movie_tv.poster_path"
              :alt="movie_tv.name + 'poster'"
            />
          </div>
          <div class="poster_placeholder" v-else>PLACEHOLDER HERE</div>
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
            :alt="`${movie_tv.original_language} country flag`"
            width="30px"
          />

          <div class="rating">
            {{ (movie_tv.vote_average * 5) / 10 }}
            <i
              class="fas fa-star"
              v-for="star in Math.round((movie_tv.vote_average * 5) / 10)"
              :key="star.id"
            ></i>

            <i
              class="far fa-star"
              v-for="emptyStar in 5 -
              Math.round((movie_tv.vote_average * 5) / 10)"
              :key="emptyStar.id"
            ></i>
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
.movie {
  margin: 2rem 0;
}
</style>