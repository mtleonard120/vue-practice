<template>
  <div id="app">
    <TodoManager />
    <PokemonFetcher />
  </div>
</template>

<script>
import PokemonFetcher from "./components/PokemonFetcher/PokemonFetcher";
import TodoManager from "./components/TodoManager/TodoManager";

export default {
  name: "app",
  components: {
    PokemonFetcher,
    TodoManager
  }
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}

#app {
  margin: 20px auto;
  max-width: 1000px;
}

#app > * {
  margin-bottom: 30px;
}
</style>
