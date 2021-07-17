<template>
  <div>
    <h2 class="title">Todos page</h2>
    <router-link class="home" to="/">Home</router-link>
    <AddTodo 
        @add-todo="addTodo"
    />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not completed</option>
    </select>
    <Loader v-if="loading"/>
    <TodoList 
    v-else-if="filteredTodos.length"
    v-bind:todos="filteredTodos"
    @remove-todo="removeTodo"
    />
    <p v-else>No current todos!</p>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import Loader from "@/components/Loader";

export default {
  name: "App",
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    };
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
        this.loading = false
      })
  },
  // watch: {
  //   filter(value) {
  //     console.log(value);
  //   }
  // },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      }
      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }
      if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      }
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList,
    AddTodo,
    Loader,
  },
};
</script>

<style scoped>
  select {
    display: block;
    margin-bottom: 60px;
    border-radius: 10px;
    padding: 5px;
    cursor: pointer;
    background-color: gainsboro;
    transition: all 0.3s ease;
    outline: none;
  }
  select:hover {
    transform: scale(1.050);
    background-color: rgb(172, 170, 170);
    color: ghostwhite;
  }
</style>