<script setup lang="ts">
import { ref } from "vue";

const todoText = ref("");

const emit = defineEmits(["addTodo", "sortTodos", "clearAll"]);

const handleSubmit = () => {
    emit("addTodo", todoText.value); // spread
    todoText.value = "";
}
</script>
<template>
  <div class="inputWrapper">
    <form @submit.prevent="handleSubmit">
      <h1>Vad vill du göra?</h1>
      <input type="text" v-model="todoText" />
      <button class="saveTodo">Spara</button>
    </form>
    <button class="sortBtn" @click="() => $emit('sortTodos')">
      Sortera A-Ö
    </button>
    <button class="clearBtn" @click="() => $emit('clearAll')">
      Rensa Allt
    </button>
  </div>
</template>
<style scoped>
.sortBtn,
.clearBtn,
.saveTodo {
  margin-left: 10px;
  margin-right: 10px;
  margin-top: 5px;
}

.inputWrapper {
    width:80%;
    border: 0.1px solid white;
    padding: 1rem;
    border-radius: 20px;
    box-shadow: 0 0 5px 0 rgb(183, 178, 178);
  
}
</style>
