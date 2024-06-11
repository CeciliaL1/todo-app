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
        <h3 :class="todo.done ? 'done' : ''">{{ todo.text }}</h3>
        <button @click="$emit('toggleTodo', todo.id)">Ändra</button>
        <button @click="$emit('removeTodo', todo.id)">Ta bort</button>
    </div>
</template>

<style scoped>
.done{ 
    text-decoration: line-through;
}
div{
    display: flex;
    flex-direction: row;
    justify-content: space-around;
}
h3 {
    text-transform: uppercase;
}
div button {
    height: 30px;
    font-family: monospace;
    text-transform: uppercase;
    letter-spacing: 1px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    padding: 8px;
    margin-top: 10px;
    background-color: lightskyblue;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
div button:hover {
    background-color: lightslategray;
    font-weight: 600;
}
</style>