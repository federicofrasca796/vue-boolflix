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
          <h2 class="title" v-if="movie_tv.name === undefined">
            {{ movie_tv.title }}
          </h2>
          <h2 v-else>{{ movie_tv.name }}</h2>
          <h3 class="og_title" v-if="movie_tv.original_name === undefined">
            {{ movie_tv.original_title }}
          </h3>
          <h3 v-else>{{ movie_tv.original_name }}</h3>
          <img
            class="lang_flag"
            :src="require(`../assets/flags/${movie_tv.original_language}.png`)"
            alt=""
            width="30px"
          />
          <!-- <div class="lang">{{ movie_tv.original_language }}</div> -->
          <div class="rating">{{ movie_tv.vote_average }}</div>
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
  methods: {},
};
</script>

<style lang="scss">
</style>