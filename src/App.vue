<template>
  <div id="app">
    <h1>ToDoリスト</h1>
    <TodoList msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'app',
  components: {
    TodoList
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
}
</style>
