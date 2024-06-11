<script setup lang="ts">
import { ref } from 'vue';
import { Todo } from '../models/Todo';
import Todos from '../components/Todos.vue'
import AddTodo from '../components/AddTodo.vue'


const todos = ref<Todo[]>([new Todo('test')]);

const addTodo = (text: string) => {
    if ( text === '') return
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
<div>
<AddTodo @add-todo="addTodo"></AddTodo>
</div>
<div><Todos :todos="todos" @toggle-todo="toggleTodo" @remove-todo="removeTodo"/></div>
</template>


<style scoped>
div{
    margin-top: 20px;

}

</style>
