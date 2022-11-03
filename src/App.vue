<template>
  <div class="container">
    <header class="text-center text-light my-4">
      <h1 class="mb-4">Vue To Do List</h1>
    </header>

    <form @submit.prevent="addToDo">
      <div class="text-center my-4">
        <label class="text-light">Add New To Do</label>
        <div class="control">
          <input
            v-model="todo"
            class="input form-control m-auto my-4"
            type="text"
            autocomplete="off"
            placeholder="Add New "
          />
        </div>
        <button
          type="submit"
          @click="addToDo"
          class="button btn btn-light my-1"
        >
          Add
        </button>
      </div>
    </form>
    <div v-for="(todo, index) in todos" :key="index">
      <ul class="list-group todos text-light my-2">
        <li
          class="
            list-group-item
            d-flex
            justify-content-between
            align-items-center
          "
        >
          <p :class="{ done: todo.done }" @click="done(todo)" class="cursor">
            <!-- {{ todo.content ? todo.content : todo }} -->
            {{ todo.content }}
          </p>
          <button
            type="button"
            class="far fa-trash-alt delete"
            @click="deleteTodo(index)"
          ></button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
const todo = ref("");
const todos = ref([]);

function addToDo() {
  if (todo.value != "") {
    todos.value.push({
      done: false,
      content: todo.value,
      id: Date.now(),
      // unique id
    });
  }
  todo.value = "";
  // input kısmı boşaltma
}

function done(todo) {
  todo.done = !todo.done;
}

function deleteTodo(index) {
  console.log("silindim", todos.value[index]);
  todos.value.splice(index, 1);
}
</script>


<style>
body {
  margin: 0;
  width: 100%;
  height: 100vh;
  background: linear-gradient(90deg, #c5e116, #ee7752, #e73c7e, #23a6d5);
  background-size: 500% 500%;
  animation: animaBG 10s ease infinite;
  /* linear infinite sonsuzluk  */
  animation-direction: alternate;
  font-family: "Montserrat";
}

@keyframes animaBG {
  0% {
    background-position: 0%;
  }

  100% {
    background-position: 100%;
  }
}

.container {
  max-width: 400px;
}

input[type-text],
input[type-text]:focus {
  color: azure;
  border: none;
  background: rgb(0, 0, 0, 0.2);
}

.todos li {
  /* background: #d3d3d3; */
  background: linear-gradient(#f8f6f9, #e3c9da);
}

.done {
  text-decoration: line-through;
}

.cursor {
  cursor: pointer;
}
</style>
