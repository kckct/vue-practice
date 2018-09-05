<template>
    <div>
        <input type="text" v-model="newTodo">
        <button @click="addTodo">add</button>
        <ul>
          <li v-for="(todo, index) in todos" :key="index" @click="removeTodo(index)">
            {{ todo.title }}
          </li>
        </ul>
    </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [{ title: "a" }, { title: "b" }],
      newTodo: ""
    };
  },

  methods: {
    addTodo() {
      var value = this.newTodo && this.newTodo.trim();
      if (!value) {
        return;
      }
      this.todos.push({
        title: value
      });
      this.newTodo = "";
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>