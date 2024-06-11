<script setup lang="ts">
import type { Todo } from '@/models/Todo';
import { defineProps } from 'vue';


type TodoPresentationProps = {
    todo : Todo;
}

defineProps<TodoPresentationProps>();

</script>

<template>
    <div>
        <h1 :class="todo.done ? 'done' : ''">{{ todo.text }}</h1>
        <button>Ändra</button>
        <button>Ta bort</button>
    </div>
</template>

<style>
.done{ 
    text-decoration: line-through;
}
</style>