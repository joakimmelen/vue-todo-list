<script setup>
import { ref } from 'vue'

const newTodo = ref("");
const todos = ref([]);

function addTodo() {
  todos.value.push({ text: newTodo.value, done: false });
  newTodo.value = "";
}

function removeTodo(todo) {
  todos.value = todos.value.filter((i) => i !== todo);
}

function doneTodo(index) {
  todos.value[index].done = true;
}
</script>

<template>
<img src="../assets/logo.png" alt="">
<div><h1>Vue TODO EXTREME /Jocke</h1></div>
<input v-model="newTodo" type="text" placeholder="Todo.." @keyup.enter="addTodo">
<button @click="addTodo">Add Todo</button>
<ul>
  <li v-for="(todo, index) in todos" :key="index">
    <input type="checkbox" v-model="todo.done">
    <span @click="doneTodo" :class="{ done: todo.done }"> {{ todo.text }} </span>
    <button @click="removeTodo(todo)">🗑️</button>
  </li>
</ul>
</template>

<style scoped>
a {
  color: #42b983;
  }

li {
  list-style: none;
   display: flex;
  margin-bottom: 5px;
  margin-left: auto;
  margin-right: auto;
  justify-content: space-between;
  width: 60%;
  font-size: 20px;
  border: 1px solid rgb(187, 187, 187)

}

.done {
  text-decoration: line-through;
  opacity: 0.3;
}
</style>
