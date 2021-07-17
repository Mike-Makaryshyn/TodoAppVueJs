<template>
  <div id="app">
    <h1 class="title">Todoshka</h1>
    <hr>
    <router-view />
  </div>
</template>

<script>

export default {
  el: "App",
  data() {
    return {
      todos: [],
    };
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  cursor: pointer;
}
.title {
  margin-bottom: 30px;
}
.home,
.todos {
  color: black;
  padding: 10px 50px;
  background-color: rgb(179, 179, 179);
  border-radius: 10px;
  text-decoration: none;
  transition: all 0.3s ease;
}
.todos:hover {
  color: rgb(255, 255, 255);
  background-color: rgb(114, 114, 114);
}
.home:hover {
  color: rgb(255, 255, 255);
  background-color: rgb(114, 114, 114);
}
</style>
