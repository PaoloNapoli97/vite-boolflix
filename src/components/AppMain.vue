<script>
import { store } from "../store";
import AppCard from "../components/AppCard.vue";

export default {
  name: "AppMain",
  components: {
    AppCard,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <main>
    <AppCard class="card" v-for="movie in store.movies" :info="movie" />
  </main>
</template>

<style lang="scss" scoped>
main {
  color: white;
  display: flex;
  flex-wrap: wrap;
  padding: 30px;

  .card {
    width: calc(100% / 6 - 20px);
    margin: 10px;
  }
}
</style>
