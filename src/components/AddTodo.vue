<script setup lang="ts">
import { ref } from "vue";

const todoText = ref("");

defineEmits(["addTodo, sortTodos, clearAll"]);
</script>
<template>
  <form @submit.prevent="() => $emit('addTodo', todoText)">
    <h1>Vad vill du göra?</h1>
    <input type="text" v-model="todoText" />
    <button class="saveTodo">Spara</button>
  </form>
  <button class="sortBtn" @click="() => $emit('sortTodos')">Sortera A-Ö</button>
  <button class="clearBtn" @click="() => $emit('clearAll')">Rensa Allt</button>
</template>
<style scoped>
.sortBtn,
.clearBtn,
.saveTodo {
  margin-left: 10px;
  margin-right: 10px;
  margin-top: 5px;
}
</style>
