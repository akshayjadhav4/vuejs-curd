<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1>Vue TODO List App</h1>
      </div>
    </div>
    <div class="row">
      <p class="display-3">Add Form</p>
    </div>
    <div class="row">
      <div class="col-12">
        <ul class="list-group">
          <Todo
            v-for="(todo,index) in todos"
            :key="index"
            :todoString="todo.todoString"
            :completed="todo.completed"
            @on-delete="deleteTodo(todo)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo.vue";
export default {
  components: {
    Todo,
  },
  data() {
    return {
      todos: [
        {
          todoString: "Learn Vue",
          completed: true,
        },
        {
          todoString: "Learn UI",
          completed: false,
        },
        {
          todoString: "Make Tea",
          completed: true,
        },
      ],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({
        todoString: newTodo,
        completed: false,
      });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    editTodo(todo, editString) {
      todo.todoString = editString;
    },
    deleteTodo(deleteTodo) {
      this.todos = this.todos.filter(
        (todo) => todo.todoString !== deleteTodo.todoString
      );
    },
  },
};
</script>

<style >
body {
  display: grid;
  place-items: center;
}
</style>