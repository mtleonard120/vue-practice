<template>
  <div class="manager">
    <div v-if="todos.length">
      <Todo
        v-for="todo in todos"
        :key="todo.id"
        :isComplete="todo.isComplete"
        :task="todo.task"
        :complete="() => completeTodo(todo.id)"
        :remove="() => removeTodo(todo.id)"
      />
    </div>
    <p v-else>All Todos Done</p>
    <hr />
    <form v-on:submit.prevent="addTodo">
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
      this.todos.push({
        id: this.nextId,
        isComplete: false,
        task: this.newTodo
      });
      this.newTodo = "";
    },
    completeTodo: function(id) {
      this.todos.find(t => t.id === id).isComplete = true;
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

.manager {
  margin: 20px auto;
  max-width: 1000px;
}
</style>
