<template>
  <TodoManager />
</template>

<script>
import TodoManager from "./components/TodoManager/TodoManager";

export default {
  name: "app",
  components: {
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
</style>
