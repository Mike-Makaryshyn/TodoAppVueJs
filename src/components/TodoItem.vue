<template>
  <li>
    <span>
      <input type="checkbox"
      v-on:change="todo.completed = !todo.completed" >
      <strong>{{ index + 1 }}</strong>
      <span 
       v-bind:class="{done: todo.completed}">{{ todo.title | uppercase }}
     </span>
    </span>
    <button class="rm" 
          v-on:click="$emit('remove-todo', todo.id)"
    >&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    }
  }
};
</script>

<style scoped>
  li {
    border: 2px solid #ccc;
    box-shadow: -3px 6px 5px 0px;
    display: flex;
    justify-content: space-between;
    padding: .5rem 1rem;
    margin-bottom: 1rem;
  }
  strong::after{
    content: ".";
    margin-right: 5px;
  }
  .rm {
    background-color: rgb(243, 86, 86);
    border-radius: 50%;
    border: none;
    font-weight: bold;
    transition: all 0.3s;
    margin-right: 10px;
  }
  .rm:hover{
    transform: scale(1.1);
    background-color: rgb(245, 41, 41);;
    color: #ccc;
  }
  .done {
    text-decoration: line-through;
  }
  input {
    cursor: pointer;
  }
</style>

