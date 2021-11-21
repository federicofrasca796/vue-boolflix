<template>
  <div class="row row-cols-1 row-cols-md-2 row-cols-lg-3 row-cols-xl-6">
    <div class="col" v-for="movie_tv in MoviesTV" :key="movie_tv.id">
      <!-- Poster  -->
      <div class="poster">
        <img
          class="w-100 h-100"
          v-if="movie_tv.poster_path != null"
          :src="'https://image.tmdb.org/t/p/w342' + movie_tv.poster_path"
          :alt="movie_tv.name + 'poster'"
        />
        <div
          class="
            poster_placeholder
            h-100
            d-flex
            flex-column
            align-items-center
            justify-content-center
          "
          v-else
        >
          <img
            class="w-50"
            src="../assets/img/no-img-placeholder.svg"
            alt="no poster avaiable"
          />
          <div>No poster avaiable</div>
        </div>
      </div>

      <!-- Title  -->
      <h2 class="title" v-if="movie_tv.name === undefined">
        {{ movie_tv.title }}
      </h2>
      <h2 v-else>{{ movie_tv.name }}</h2>

      <!-- Original Title  -->
      <i class="og_title" v-if="movie_tv.original_name === undefined">
        {{ movie_tv.original_title }}
      </i>
      <i v-else>{{ movie_tv.original_name }}</i>

      <!-- Language flag  -->
      <img
        class="lang_flag"
        :src="require(`../assets/flags/${movie_tv.original_language}.png`)"
        :alt="`${movie_tv.original_language} country flag`"
        width="30px"
      />

      <!-- Star Rating  -->
      <div class="rating">
        {{ (movie_tv.vote_average * 5) / 10 }}
        <i
          class="fas fa-star"
          v-for="star in Math.round((movie_tv.vote_average * 5) / 10)"
          :key="star.id"
        ></i>

        <i
          class="far fa-star"
          v-for="emptyStar in 5 - Math.round((movie_tv.vote_average * 5) / 10)"
          :key="emptyStar.id"
        ></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    MoviesTV: Array,
  },
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";
.poster {
  width: 100%;
  height: 439px;
  & > img {
    object-fit: cover;
  }
  .poster_placeholder {
    background: $dark_grey;
    color: $light_grey;
    img {
      padding: 0.5rem;
      margin-bottom: 0.5rem;
    }
  }
  & > img,
  .poster_placeholder {
    border-radius: 5px;
  }
}
</style>