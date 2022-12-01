<script>
import axios from "axios";
import { store } from "../store";

import SearchBar from "./SearchBar.vue";
import BoolfixLogo from "./BoolfixLogo.vue";

export default {
  name: "AppHeader",
  components: {
    BoolfixLogo,
    SearchBar,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    movieData() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "e8df3c911b3a0c278ba5b8289d5a4a43",
            query: this.store.titleSearch,
            language: "it-IT",
          },
        })
        .then((resp) => {
          this.store.movies = resp.data.results;
        });
    },
  },
};
</script>

<template>
  <header>
    <BoolfixLogo />
    <SearchBar @performSearch="movieData" />
  </header>
</template>

<style lang="scss" scoped>
header {
  padding: 10px;
  background-image: linear-gradient(#060606, #141414);
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
