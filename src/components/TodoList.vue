<template>
  <div>
    <input type="radio" id="one" value="One" v-model="picked">全て
    <input type="radio" id="one" value="One" v-model="picked">作業中
    <input type="radio" id="one" value="One" v-model="picked">完了
    <table>
      <tbody>
        <th>ID</th>
        <th>コメント</th>
        <th colspan="2">状態</th>
        <tr v-for="todo in todos" v-bind:key="todo.id">
          <td>{{ todo.id }}</td>
          <td>{{ todo.comment }}</td>
          <td>{{ todo.state }}</td>
        </tr>
      </tbody>
    </table>
    <h2>新規タスクの追加</h2>
    <input type="text" class="input" v-model="inputTodo">
    <button @click="addTodo">追加</button>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      inputTodo: "",
      todos: [{ id:0,comment: "def",state:"b" }]
    };
  },
  methods: {
    addTodo: function() {
      this.todos.push({ title: this.inputTodo });
    }
  }
};
</script>

<style scoped>
</style>
