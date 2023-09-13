<template>
  <div class="bg-gray-500 min-h-screen flex justify-center items-center">
    <div class="bg-white p-4 rounded w-96">
      <h1 class="text-2xl font-semibold mb-10 underline text-center">
        To-Do APP
      </h1>
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
          <input v-model="todo.completed" type="checkbox" class="text-start" />

            <label class="text-center justify-center items-center pl-2">
              {{ todo.title }}</label
            >
            <!-- <button
              @click="editTodo(todo)"
              class="text-blue-500 hover:text-blue-800 cursor-pointer text-xl pr-4 ml-[30%]"
            >
              Edit
            </button> -->
            <button
              @click="removeTodo(todo)"
              class="text-red-700 hover:text-red-800 cursor-pointer text-3xl"
            >
              &times;
            </button>
          
          <!-- <template v-else>
            <input
              v-model="todo.editedTitle"
              @keyup.enter="savedEditedTodo(todo, index)"
              class="w-10/12 p-2 rounde-1 outline-black"
              type="text"
            />
            <button
              @click="savedEditedTodo(todo, index)"
              class="w-2/12 bg-green-400 text-black rounded-r p-2 hover:bg-green-700 cursor-pointer ml-4 rounded-sm"
            >
              Save
            </button>
        </template> -->
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
const STORAGE_KEY = "tasks"; //store tasks in local storage
import { ref } from "vue";

const newTodo = ref(""); //input field where users enter newtask
const todos = ref([]); //it stores the todo items

//to retrive the data
todos.value = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");


// add new task in todos
const addTodo = () => {
  todos.value.push({
    id: todos.value.length,
    title: newTodo.value,
    completed: "false",
  });
  newTodo.value = ""; //clears input field
  localStorage.setItem(STORAGE_KEY, JSON.stringify(todos.value)); //updates storage with new todos
//   console.log(todos);
//   console.log(todos.value);
};

//delete the task
const removeTodo = (todo) => {
  alert("delete the task?");
  todos.value.splice(todos.value.indexOf(todo), 1);
  localStorage.setItem(STORAGE_KEY, JSON.stringify(todos.value));
};

// const editTodo = (todo) => {
//   todo.editing = true;
//   todo.editedTitle = todo.title;
// };

// const savedEditedTodo = (todo, index) => {
//   todo.title = todo.editedTitle;
//   todo.editing = false;
//   localStorage.setItem(STORAGE_KEY, JSON.stringify(todos.value));
// };
// todos.value.forEach((todo) => {
//   todo.editing = false;
//   todo.editedTitle = "";
// });
</script>
