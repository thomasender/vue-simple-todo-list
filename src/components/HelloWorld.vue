<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string, age: number }>()

const toDos = ref<string[]>([])


function addTodo(todo: string) {
  toDos.value.push(todo)
}

function clearTodos() {
  toDos.value = []
}

function deleteTodo(index) {
  toDos.value.splice(index, 1)
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <div class="card">
    <input type="text" v-model="todo" />
    <button @click="addTodo(todo)">Add</button>
    <ul>
      <li v-for="(todo, index) in toDos">
        <span>{{ todo }}</span>
        <button @click="deleteTodo(index)">Delete</button>
      </li>
    </ul>
    <p v-if="toDos.length === 0">Add a Todo</p>
    <button v-else @click="clearTodos()">Clear All Todos</button>
  </div>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
