<script setup lang="ts">
import { ref } from 'vue';
import { Todo } from '../models/Todo';
import Todos from '../components/Todos.vue'
import AddTodo from '../components/AddTodo.vue'


const todos = ref<Todo[]>([]);

const addTodo = (text: string) => {
todos.value.push(new Todo(text))
};

const toggleTodo = (id:number) => {
   const foundTodo = todos.value.find((todo )=> todo.id === id)
   if (foundTodo) {
    foundTodo.done = !foundTodo.done
   }
};

const removeTodo = (id: number) => {
    const foundPosition = todos.value.findIndex((todo) => todo.id === id);
    todos.value.splice(foundPosition, 1)
}

</script>

<template>
<AddTodo @add-todo="addTodo"></AddTodo>
<Todos :todos="todos" @toggle-todo="toggleTodo" @remove-todo="removeTodo"/>
</template>