<script setup lang="ts">
import { ref } from 'vue';

const todoText = ref("");

defineEmits(["addTodo"])

</script>
<template>

    <form @submit.prevent="() => $emit('addTodo', todoText)">
        <h1>Todo List</h1>
        <input v-model="todoText" />
        <button>Spara</button>
     </form>

</template>
<style>
</style>
