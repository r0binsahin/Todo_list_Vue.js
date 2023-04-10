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

    <span class="buttons">
      <button class="checkBtn" @click="() => $emit('toggleTodo')">
        <i id="checkIcon" class="bi bi-check-square-fill"></i>
      </button>
      <button class="dltBtn" @click="() => $emit('removeTodo', 'index')">
        <i id="dltIcon" class="bi bi-x-circle"></i>
      </button>
    </span>
  </div>
</template>
<style scoped>
.todoContainer {
  width: 80%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  border-radius: 10px;
  box-shadow: 0 0 5px 0 rgb(183, 178, 178);
  margin-top: 10px;
}
.done {
  text-decoration: line-through;
}

.buttons {
  display: flex;
  flex-direction: row;
  place-items: center;
  padding: 10px;
}

.dltBtn, .checkBtn {
  border-style: none;
  background-color: #efa9ae;
  display: flex;
  flex-direction: row;
  place-items: center;
  width: 25px;
  height: 25px;
  border-radius: 15%;
  cursor: pointer;
}
.checkBtn {
  background-color: #b7e3cc;
  margin-right: 10px;
}

.checkBtn:hover {
  background-color: #6ddaa1;
}

#checkIcon, #dltIcon {
  color: white;
}

.dltBtn:hover  {
  background-color: #f08c92;
}

p {
margin-left: 10px;
}

@media screen and (min-width: 768px){

  .todoContainer {
  width: 30%;
}
   
 }

</style>
