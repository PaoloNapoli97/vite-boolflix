<script>
import { store } from "../store";

export default {
  name: "SearchBar",
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div>
    <form @submit.prevent="$emit('performSearch')">
      <input
        type="text"
        placeholder="Cerca: Titoli, generi, film"
        v-model="store.titleSearch"
      />
      <button type="submit">Cerca</button>
    </form>
  </div>
</template>

<style lang="scss" scoped>
input[type="text"] {
  color: white;
  background: none;
  border: 1px solid white;
  outline: none;
  padding: 4px;
  margin-right: 10px;
}
button {
  padding: 4px;
}
</style>
