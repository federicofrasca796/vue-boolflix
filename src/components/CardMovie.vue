<template>
  <div class="row row-cols-1 row-cols-md-2 row-cols-lg-3 row-cols-xl-5">
    <!-- {{ MoviesTV }} -->
    <div class="col" v-for="movie_tv in MoviesTV" :key="movie_tv.id">
      <!-- Poster  -->
      <div class="movie_card position-relative pb-5">
        <!-- Poster -->
        <div class="poster">
          <img
            class="w-100 h-100"
            v-if="movie_tv.poster_path != null"
            :src="'https://image.tmdb.org/t/p/w342' + movie_tv.poster_path"
            :alt="movie_tv.name || movie_tv.title + 'poster'"
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

        <!-- Info on hover -->
        <div
          class="
            movietv_info
            position-absolute
            top-0
            left-0
            w-100
            p-3
            flex-column
            justify-content-between
          "
        >
          <div>
            <!-- Title  -->
            <h2 class="title" v-if="movie_tv.name === undefined">
              {{ movie_tv.title }}
            </h2>
            <h2 v-else>{{ movie_tv.name }}</h2>

            <!-- Original Title  -->
            <div
              v-if="
                movie_tv.original_name != movie_tv.name ||
                movie_tv.original_title != movie_tv.title
              "
            >
              <i class="og_title" v-if="movie_tv.original_name === undefined">
                {{ movie_tv.original_title }}
              </i>
              <i v-else>{{ movie_tv.original_name }}</i>
            </div>

            <!-- Star Rating  -->
            <div class="rating my-2">
              <i
                class="fas fa-star me-1"
                v-for="star in Math.round((movie_tv.vote_average * 5) / 10)"
                :key="star.id"
              ></i>

              <i
                class="fas fa-star empty_star me-1"
                v-for="emptyStar in 5 -
                Math.round((movie_tv.vote_average * 5) / 10)"
                :key="emptyStar.id"
              ></i>
              {{ (movie_tv.vote_average * 5) / 10 }}
            </div>

            <!-- Language flag  -->
            <img
              class="lang_flag"
              v-if="flags.includes(movie_tv.original_language)"
              :src="
                require(`../assets/flags/${movie_tv.original_language}.png`)
              "
              :alt="`${movie_tv.original_language} country flag`"
            />
            <div v-else>{{ movie_tv.original_language }}</div>
          </div>

          <!-- Movie/Tv show overview -->
          <div class="overview my-3">
            <p>
              {{ movie_tv.overview.substring(-1, 200) }}
              <span v-if="movie_tv.overview.length > 200">...</span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    MoviesTV: Array,
  },
  data() {
    return {
      flags: [
        "aa",
        "ab",
        "af",
        "ar",
        "as",
        "az",
        "be",
        "bg",
        "bm",
        "bo",
        "bs",
        "cn",
        "cs",
        "cy",
        "da",
        "de",
        "el",
        "en",
        "es",
        "et",
        "fa",
        "fi",
        "fo",
        "fr",
        "ga",
        "gu",
        "he",
        "hi",
        "hr",
        "hu",
        "hy",
        "id",
        "is",
        "it",
        "ja",
        "ka",
        "kk",
        "km",
        "kn",
        "ko",
        "ku",
        "la",
        "lt",
        "lv",
        "mk",
        "ml",
        "mn",
        "mr",
        "ms",
        "mt",
        "ne",
        "nl",
        "no",
        "pa",
        "pl",
        "pt",
        "ro",
        "ru",
        "sh",
        "sk",
        "sl",
        "sq",
        "sr",
        "sv",
        "ta",
        "te",
        "tk",
        "tl",
        "tr",
        "uk",
        "ur",
        "vi",
        "xh",
        "xx",
        "zh",
      ],
    };
  },
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

.poster {
  width: 100%;
  height: 554px;
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
  .poster,
  .poster_placeholder {
    transition: opacity 0.2s;
  }
}
.empty_star {
  color: $dark_grey;
}
.movie_card .poster,
.movie_card .poster_placeholder {
  transition: opacity 0.2s, transform 0.1s;
}
.movie_card:hover .movietv_info {
  display: flex;
}
.movie_card:hover .poster,
.movie_card:hover .poster_placeholder {
  opacity: 0.3;
  transform: scale(102%);
}
.movietv_info {
  display: none;
  padding: 1rem;
  height: 554px;
  //   overflow-y: auto;
  .lang_flag {
    width: 40px;
    border-radius: 5px;
  }
  .overview {
    height: 120px;
    p {
      height: 100%;
      overflow-y: auto;
    }
  }
}
</style>