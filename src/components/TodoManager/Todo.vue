<template>
  <div class="todo-line">
    <div :class="[isComplete ? 'complete' : '']" class="todo">{{ task }}</div>
    <div class="buttons">
      <button @click="complete">Complete</button>
      <button @click="remove">Remove</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: {
    isComplete: Boolean,
    remove: Function,
    task: String
  },
  methods: {
    complete: function() {
      this.$emit("update:isComplete", true);
    }
  }
};
</script>

<style scoped>
.buttons {
  display: flex;
}

.complete {
  text-decoration: line-through;
}

.todo-line {
  width: 300px;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
}
</style>
