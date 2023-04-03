<script setup lang="ts">
import { ref } from 'vue';
import { Todo } from '../models/Todo';

const todos = ref<Todo[]>([]);
const userInput = ref("");

const addToLocalStorage = ()=> {
    localStorage.setItem("todolist", JSON.stringify(todos.value))
}

const toggleTodo = (i: number) => {
    todos.value[i].done = !todos.value[i].done;
    addToLocalStorage()
}

const handleSubmit = ()=>{
    todos.value.push (new Todo(userInput.value, false))
    addToLocalStorage()
    userInput.value = "";
}
const deleteTodo = (i:number)=>{
    todos.value.splice(i, 1);
    addToLocalStorage()
}

const toggleButtonInnerText = (i:number) =>{
    const state = todos.value[i].done ? 'ej utfört' : 'utfört';
    return state
}


const todosLS: Todo[] = JSON.parse(localStorage.getItem("todolist") || "[]")
console.log(todosLS)



</script>

<template>
    <h1>todo list</h1>
    <form @submit.prevent="handleSubmit">
        <input type="text" v-model = "userInput" placeholder="skriv in ett ärende..."/>
        <button>spara</button>
    </form>


    <ul>
        <li
        v-for ="(todo, index) in todos"
        :key = "index"
        class="todo"
        :class="todo.done ? 'done' : ' '"
        >
            {{ todo.todoText }}
            <button @click="toggleTodo(index)" v-text="toggleButtonInnerText(index)"></button>
            <button @click="deleteTodo(index)">ta bort</button>
    </li>
    </ul>
</template>

<style scoped>
.todo.done {
    text-decoration: line-through;
}
</style>
