<script setup lang="ts">
import { ref } from 'vue';
import { Todo } from '../models/Todo';
import ShowTodos from './ShowTodos.vue';
import AddTodo from './AddTodo.vue';

const todos = ref<Todo[]>(JSON.parse(localStorage.getItem("todos") || "[]"));

const handleToggle = (i: number) =>{
    todos.value[i].done = !todos.value[i].done;
    saveToLS(todos.value)
    sortDoneTodos()
}

const addTodo = (todoText: string)=>{
    todos.value.push(new Todo(todoText, false))
    saveToLS(todos.value)

}

const saveToLS = (todos: Todo[])=>{ 
    localStorage.setItem("todos", JSON.stringify(todos));
}

const removeTodo = (i: number)=>{
    todos.value.splice(i, 1);
    saveToLS(todos.value)
}

const sortTodos = ()=>{
     todos.value.sort((a: Todo, b: Todo)=> a.todoText >b.todoText ?  1 :  -1) 
     sortDoneTodos()

    console.log(todos.value)
}

const clearAll = ()=>{
    localStorage.clear();
    window.location.reload();
}

const sortDoneTodos = ()=>{
    todos.value.sort((a: Todo, b: Todo) => a.done - b.done)
}


</script>
<template>
    <AddTodo @addTodo="addTodo" @sort-todos="sortTodos" @clear-all="clearAll"></AddTodo>
    <ShowTodos :todo ="todo" v-for = "(todo, index ) in todos " @toggle-todo ="()=> handleToggle(index)" @remove-todo="()=> removeTodo(index)" :key = "index">
    </ShowTodos>
</template>
<style>
</style>
