<template>
  <div id="app">
    <div class="container">
      <div class="todo-list">
        <Todo
          v-for="todo in todos"
          :key="todo.id"
          :task="todo.task"
          :remove="() => removeTodo(todo.id)"
          :id="todo.id"
        />
      </div>
      <form v-on:submit.prevent="addTodo">
        <input type="text" v-model="newTodo" placeholder="Add New Todo Task" />
        <button type="submit">Add Todo</button>
      </form>
    </div>
  </div>
</template>

<script>
import Todo from "./components/Todo";

export default {
  name: "app",
  data: () => ({
    newTodo: "",
    todos: [
      {
        id: 1,
        task: "Eat"
      },
      {
        id: 2,
        task: "Poop"
      }
    ]
  }),
  computed: {
    nextId: function() {
      if (this.todos.length === 0) {
        return 1;
      }
      const idArr = this.todos.map(t => t.id);
      return Math.max(...idArr) + 1;
    }
  },
  components: {
    Todo
  },
  methods: {
    addTodo: function() {
      this.todos.push({ id: this.nextId, task: this.newTodo });
    },
    removeTodo: function(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    }
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

.container {
  display: flex;
}

.todo-list {
  width: 200px;
}
</style>
