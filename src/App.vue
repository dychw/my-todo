<template>
  <div id="app">
    <h1>ToDoリスト</h1>
    <TodoList></TodoList>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",
  components: {
    TodoList
  }
};
</script>

<style>

</style>
