<template>
  <div id="app">
    <div>
      <button @click="addTodo">Add Todo</button>
    </div>
    <Todo v-for="todo in todos" :key="todo.id" :task="todo.task" />
  </div>
</template>

<script>
import Todo from "./components/Todo";

export default {
  name: "app",
  data: () => ({
    todos: [
      {
        id: 1,
        task: "Eat"
      },
      {
        id: 2,
        task: "Poop"
      }
    ],
    latestId: 2
  }),
  components: {
    Todo
  },
  methods: {
    addTodo: function() {
      this.latestId++;
      this.todos.push({ id: this.latestId, task: "newThing" });
    }
  }
};
</script>
