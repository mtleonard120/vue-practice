<template>
  <div class="fetcher">
    <h2>Pokemon Fetcher</h2>
    <input type="text" v-model="query" placeholder="Search Pokemon by #" />
    <div v-if="loading">Loading...</div>
    <div v-else-if="errorMessage" class="error">Error: {{ errorMessage }}</div>
    <div v-else-if="pokemonName">Pokemon Found: {{ pokemonName }}</div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PokemonFetcher",
  data: () => ({
    errorMessage: "",
    loading: false,
    pokemonName: "",
    query: ""
  }),
  watch: {
    query: function(newQuery, oldQuery) {
      this.pokemonName = "";
      this.errorMessage = "";

      if (newQuery && newQuery !== oldQuery) {
        this.loading = true;

        axios
          .get("https://pokeapi.co/api/v2/pokemon/" + this.query)
          .then(res => {
            this.pokemonName = res.data.name;
          })
          .catch(res => {
            this.errorMessage = res.message;
          })
          .finally(() => {
            this.loading = false;
          });
      }
    }
  }
};
</script>

<style scoped>
.error {
  padding: 5px 0;
  color: red;
}
.fetcher {
  padding: 20px;
  padding-top: 0;
  border: 1px solid black;
}
</style>
