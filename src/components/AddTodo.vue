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
    <input type="text" v-model="todoText">
    <button>Spara</button>
</form>

</template>

<style scoped>

</style>