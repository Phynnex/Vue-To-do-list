<template>
<!-- Code along with coding garden youtube -->
  <div id="app" >
    <div class="header">
      <h1 class="header">Todo App + Composition API</h1>
    <div id="nav" >
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>
    </div>
    </div>
    
    <form @submit.prevent="addNewTodo">
      <label>New Todo</label>
      <input v-model="newTodo" type="text" name="newTodo">
      <button>Add new list</button>
    </form> 
    <button @click="removeAllTodos">Remove All</button>
  <button @click="markAllDone">Mark All Done</button>
    <ul>
      <li v-for="todo in todos" :key="todo.id" class="todo">
        <h3 :class="{ done: todo.done }" @click="toggleDone(todo)">{{todo.content}}</h3>
      </li>
    </ul>
    
  </div>
  
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const newTodo = ref('');
    const todos = ref([]);

    function addNewTodo() {
      todos.value.push({
        id: Date.now(),
        done: false,
        content: newTodo.value,
      });
      newTodo.value = '';
    }

    function toggleDone(todo) {
      todo.done = !todo.done;
    }

    function removeTodo(index) {
      todos.value.splice(index, 1);
    }

    function markAllDone() {
      todos.value.forEach((todo) => todo.done = true);
    }

    function removeAllTodos() {
      todos.value = [];
    }


    return {
      todos,
      newTodo,
      addNewTodo,
      toggleDone,
      removeTodo,
      markAllDone,
      removeAllTodos,
    }
  }
}
</script>

<style scoped>
  body{
    font-family: sans-serif;
    padding-bottom: 1em;
    padding-top: 1em;
    font-size: 2em;
    width: 80%;
    margin: 0 auto;
  }
  input, textarea, button, p, div, section, article, select {
    display: 'block';
    width: 100%;
    font-family: sans-serif;
    margin: 0.5em;
    font-size: 1em;
  }
  .todo{
    cursor: pointer;
  }
  .done {
    text-decoration: line-through;
  }

</style>