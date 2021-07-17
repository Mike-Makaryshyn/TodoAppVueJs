<template>
   <form @submit.prevent="onSubmit">
      <input type="text" v-model="title">
      <button type="submit">Create</button>
   </form>
</template>

<script>
export default {
   data() {
      return {
         title: ''
      }
   },
   methods: {
      onSubmit() {
         console.log(this.title);
         if (this.title.trim()) {
            const newTodo = {
               id: Date.now(),
               title: this.title,
               completed: false
            }

            this.$emit('add-todo', newTodo)
            this.title = ''
         }
      }
   }
}
</script>

<style scoped>
   form {
      display: flex;
      margin-bottom: 20px;
   }
   input {
      width: 400px;
      outline: none;
      margin-right: 10px;
      padding: 10px;
      border-radius: 10px;
      outline: none;
      border: 2px solid #ccc;
      transition: all 0.3s;
   }
   input:focus {
      border: 2px solid rgb(153, 153, 153);
   }
   button {
      background-color: rgb(118, 124, 141);
      color: azure;
      border: none;
      border-radius: 10px;
      padding: 10px 30px;
      transition: all 0.3s;
      font-weight: bold;
   }
   button:hover{
      transform: scale(1.05);
      color: black;
      background-color: rgb(166, 171, 184);;
   }
</style>