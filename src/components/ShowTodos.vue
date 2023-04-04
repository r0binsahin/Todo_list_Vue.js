<script setup lang="ts">
import { Todo } from '../models/Todo';

    interface IShowTodoProps {
        todo: Todo;
    }


    defineProps<IShowTodoProps>();
    defineEmits(["toggleTodo", "removeTodo"]);

</script>
<template>
    <div>
        <p :class ="todo.done ? 'done' : ' ' ">{{ todo.todoText}}</p>
        <input  class="checkBtn" type="checkbox" @click="() => $emit('toggleTodo')">
        <button class= "dltBtn" @click="()=> $emit('removeTodo','index' )"><i class="bi bi-x-circle"></i></button>
    </div>
   

</template>
<style scoped>

.done {
    text-decoration: line-through;
}

.dltBtn, .checkBtn {
    padding: 0;
    margin: 2px;
}


</style>
