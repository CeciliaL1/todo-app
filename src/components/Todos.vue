<script setup lang="ts">
import type { Todo } from '@/models/Todo';
import {defineProps }from 'vue';
import TodoPresentation from '../components/TodoPresentation.vue'

interface ITodosProps {
    todos: Todo[];
}

const props = defineProps<ITodosProps>()

</script>

<template>
<div class="todos">
    <TodoPresentation v-for="todo in todos" :key="todo.id" :todo="todo">
     
    </TodoPresentation>
</div>
</template>

<style scoped>
</style>