<script setup lang="ts">
import { Todo } from "../models/Todo";

interface IShowTodoProps {
  todo: Todo;
}

defineProps<IShowTodoProps>();
defineEmits(["toggleTodo", "removeTodo", "sortTodo"]);
</script>
<template>
  <div class="todoContainer">
    <p :class="todo.done ? 'done' : ' '">{{ todo.todoText }}</p>
    <button
      class="checkBtn"
      @click="() => $emit('toggleTodo')"
    ><i class="bi bi-check-square-fill"></i></button>
    <button class="dltBtn" @click="() => $emit('removeTodo', 'index')">
      <i class="bi bi-x-circle"></i>
    </button>
  </div>
</template>
<style scoped>
.todoContainer {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
.done {
  text-decoration: line-through;
}

.dltBtn {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 25px;
  height: 25px;
  margin: 10px;
}
.checkBtn {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 25px;
  height: 25px;
  margin: 10px;
}

/* .bi {
    width: 20px;
    height: 20px;
} */
</style>
