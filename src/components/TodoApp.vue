<script setup lang="ts">
import {ref } from 'vue';
import {Todo} from '../models/Todo';
import Todos from '../components/Todos.vue'
import AddTodo from '../components/AddTodo.vue'

const todos = ref<Todo[]>([new Todo('Learn Props'), new Todo('Learn emits')]);

const addTodo = (text: string) => {
todos.value.push(new Todo(text))
};

</script>

<template>
<AddTodo @add-todo="addTodo"></AddTodo>
<Todos :todos="todos"/>
</template>