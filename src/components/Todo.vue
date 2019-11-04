<template>
  <div>
    <div class="todo">{{ task }}</div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: {
    task: String
  }
};
</script>
