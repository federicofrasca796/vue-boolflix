<template>
  <main id="site_main">
    <div class="container-fluid px-5">
      <!-- <div v-if="this.emptyArr === true">0 Movies found</div> -->
      <div>
        <cardMovie :MoviesTV="MoviesTVArr" />
      </div>
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