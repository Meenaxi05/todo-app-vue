<template>
  <div class="bg-gray-500 min-h-screen flex justify-center items-center">
    <div class="bg-white p-4 rounded w-96">
      <h1 class="text-2xl font-semibold mb-10 underline text-center">To-Do APP</h1>
      <div class="flex">
        <input
          v-model="newTodo"
          v-on:keyup.enter="addTodo"
          class="w-10/12 p-2 rounded-1 outline-black"
          type="text"
          placeholder="Enter Task"
        />
        <button
          @click="addTodo"
          class="w-2/12 bg-gray-400 text-black rounded-r p-2 hover:bg-gray-700 cursor-pointer ml-4 rounded-sm"
        >
          ADD
        </button>
      </div>
      <ul class="mt-4">
        <li v-for="todo in todos" class="flex items-center p-2 border-b">
          
            <input
              v-model="todo.completed"
              type="checkbox"
              class="text-start"
            />
            <label class="text-center justify-center items-center">{{ todo.title }}</label>
            <button
            @click="removeTodo(todo)"
              class="text-red-700 hover:text-red-800 cursor-pointer text-xl"
            >
              &times;
            </button>
          
        </li>
      </ul>
    </div>
  </div>
</template>


<script setup>
const STORAGE_KEY = 'tasks'
import { ref } from "vue";

const newTodo = ref("");
const todos = ref([])

    todos.value = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]')

const addTodo = () => {
  todos.value.push({
    id: todos.value.length,
    title: newTodo.value,
    completed: "false",
  });
  newTodo.value = ""
  localStorage.setItem(STORAGE_KEY, JSON.stringify(todos.value))
  console.log(todos);
  console.log(todos.value);
};

const removeTodo = (todo)  => {
alert('delete the todo task')
todos.value.splice(todos.value.indexOf(todo), 1)
localStorage.setItem(STORAGE_KEY, JSON.stringify(todos.value))
}
</script>
