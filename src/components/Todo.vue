<template>
  <div class="todo-line">
    <div class="todo">{{ task }}</div>
    <button @click="remove">Remove</button>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: {
    id: Number,
    remove: Function,
    task: String
  }
};
</script>

<style scoped>
.todo-line {
  width: 100%;
  padding: 0 20px;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
}
</style>
