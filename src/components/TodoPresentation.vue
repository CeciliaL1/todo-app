<script setup lang="ts">
import type { Todo } from '@/models/Todo';
import { defineProps, defineEmits } from 'vue';


type TodoPresentationProps = {
    todo : Todo;
}

defineProps<TodoPresentationProps>();

const emit = defineEmits<{
    (e: "toggleTodo", id: number):void;
    (e: 'removeTodo', id: number):void;
}>();

</script>

<template>
    <div>
        <h1 :class="todo.done ? 'done' : ''">{{ todo.text }}</h1>
        <button @click="$emit('toggleTodo', todo.id)">Ändra</button>
        <button @click="$emit('removeTodo', todo.id)">Ta bort</button>
    </div>
</template>

<style>
.done{ 
    text-decoration: line-through;
}
</style>