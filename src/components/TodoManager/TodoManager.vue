<template>
  <div class="manager">
    <h2>Todo Manager</h2>
    <div v-if="todos.length">
      <Todo
        v-for="todo in todos"
        v-bind.sync="todo"
        :key="todo.id"
        :remove="() => removeTodo(todo.id)"
      />
    </div>
    <p v-else>All Todos Done</p>
    <hr />
    <form v-on:submit.prevent="addTodo">
      <div class="error" v-if="errorMessage">{{ errorMessage }}</div>
      <input type="text" v-model="newTodo" placeholder="Add New Todo Task" />
      <button type="submit">Add Todo</button>
    </form>
  </div>
</template>

<script>
import Todo from "../TodoManager/Todo";

export default {
  name: "todo-manager",
  data: () => ({
    errorMessage: "",
    newTodo: "",
    todos: [
      {
        id: 1,
        isComplete: false,
        task: "Eat"
      },
      {
        id: 2,
        isComplete: false,
        task: "Drink"
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
      if (!this.newTodo) {
        this.errorMessage = "Please enter a todo task.";
        return;
      } else {
        this.errorMessage = "";
        this.todos.push({
          id: this.nextId,
          isComplete: false,
          task: this.newTodo
        });
        this.newTodo = "";
      }
    },
    removeTodo: function(id) {
      this.todos = this.todos.filter(t => t.id !== id);
    }
  }
};
</script>

<style scoped>
.error {
  padding: 5px 0;
  color: red;
}
.manager {
  padding: 20px;
  padding-top: 0;
  border: 1px solid black;
}
</style>
