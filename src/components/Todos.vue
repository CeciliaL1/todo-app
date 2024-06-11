<script setup lang="ts">
import type { Todo } from '@/models/Todo';
import {defineProps, defineEmits }from 'vue';
import TodoPresentation from '../components/TodoPresentation.vue'

interface ITodosProps {
    todos: Todo[];
}

const props = defineProps<ITodosProps>();

defineEmits<{
    (e: 'toggleTodo', id: number):void;
    (e: 'removeTodo', id: number):void
}>();


</script>

<template>
<div class="todos">
    <TodoPresentation 
    v-for="todo in todos" 
    :key="todo.id" 
    :todo="todo"
    @toggle-todo="(id:number) => $emit('toggleTodo', id)"
    @remove-todo="(id:number) => $emit('removeTodo', id)">
     
    </TodoPresentation>
</div>
</template>

<style scoped>

</style>