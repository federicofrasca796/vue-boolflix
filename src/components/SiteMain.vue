<template>
  <main id="site_main">
    <div class="container-fluid px-5">
      <!-- Movie/TV show card  -->
      <cardMovie :MoviesTV="MoviesTVArr" />
    </div>
  </main>
</template>

<script>
import cardMovie from "./CardMovie.vue";

export default {
  components: {
    cardMovie,
  },
  props: {
    MoviesTVArr: Array,
  },
};
</script>

<style lang="scss">
.movie {
  margin: 2rem 0;
}
</style>