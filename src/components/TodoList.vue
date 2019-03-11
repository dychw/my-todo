<template>
  <div>
    <label v-for="filter in filters" :key="filter.id">
      <input type="radio" v-model="selectedFilter" :value="filter.label">
      {{filter.label}}
    </label>
    <table>
      <tbody>
        <th>ID</th>
        <th>コメント</th>
        <th>状態</th>
        <tr v-for="todo in filterTodos" :key="todo.id">
          <td>{{ todo.id }}</td>
          <td>{{ todo.title }}</td>
          <td>
            <button @click="todo.state='完了'">{{todo.state}}</button>
          </td>
          <td>
            <button @click="removeTodo(todo.id)">削除</button>
          </td>
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
      todos: [],
      filters: [{ label: "すべて" }, { label: "作業中" }, { label: "完了" }],
      selectedFilter: "すべて"
    };
  },
  methods: {
    addTodo: function() {
      if (this.inputTodo.match(/^\s*$/) === null) {
        var id_max = Math.max.apply(
          Math,
          this.todos.map(function(o) {
            return o.id;
          })
        );
        this.todos.push({
          id: this.todos.length === 0 ? 0 : id_max + 1,
          title: this.inputTodo,
          state: "作業中"
        });
        this.inputTodo = "";
      }
    },
    removeTodo: function(id) {
      this.todos.splice(id, 1);
    }
  },
  computed: {
    filterTodos: function() {
      return this.todos.filter(function(el) {
        return this.selectedFilter === "すべて"
          ? true
          : this.selectedFilter === el.state;
      }, this);
    }
  }
};
</script>

<style scoped>
</style>
