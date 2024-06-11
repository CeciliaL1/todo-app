<script setup lang="ts">
import { defineEmits, ref } from 'vue' ;

const todoText = ref('');


const handleSubmit = () => {
    emit('addTodo',todoText.value)
    todoText.value = '';
};

const emit = defineEmits<{
    (e: "addTodo", text: string):void;
}>(); 
 
</script> 

<template>
  
<form @submit.prevent="handleSubmit">
    <h1>Add a task</h1>
    <input type="text" v-model="todoText">
    <button>Spara</button>
</form>

</template>

<style scoped>
form {
    margin-right: 50px;
}
h1{
    margin: 5px
}
input {
    height: 30px;
    border: none;
    border-radius: 6px;
    margin: 5px;
    cursor: pointer;
    outline: none;
}
input:hover {
    background-color: lightslategray;
}
input:focus {
    background-color: lightgreen;
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
    background-color: lightskyblue;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
div button:hover {
    background-color: lightslategray;
    font-weight: 600;
}

</style>