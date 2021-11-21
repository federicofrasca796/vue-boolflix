<template>
  <header id="site_header">
    <div
      class="
        container-fluid
        d-flex
        justify-content-between
        align-items-center
        px-5
      "
    >
      <!-- LOGO -->
      <img src="../assets/img/netflix-logo.svg" alt="logo" class="h-50" />

      <!-- Search Bar  -->
      <div class="search_bar">
        <input
          placeholder="Titles, actors, genre"
          v-model="inputSearch"
          @keyup.enter="$emit('input-movie', inputSearch)"
        />
        <button @click="$emit('input-movie', inputSearch)" class="ms-3">
          <i class="fas fa-search"></i>
        </button>
      </div>
    </div>
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

<style lang="scss">
@import "../assets/scss/variables.scss";

#site_header {
  background: $dark_gradient_0;
  .container-fluid {
    height: 80px;
  }
  position: sticky;
  top: 0;
}

.search_bar {
  input {
    transition: border 0.2s;
    &:focus-visible {
      border: 1px solid $dark_grey;
      outline: none;
    }
  }
  button {
    font-size: 1.3rem;
    background: none;
    border: none;
    color: #ffff;
    transition: color 0.2s;
    &:hover {
      color: $light_grey;
    }
  }
}
</style>