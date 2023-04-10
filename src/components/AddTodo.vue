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
      <h1>vad vill du göra?</h1>
      <input class= "textBox" type="text" v-model="todoText"  placeholder="lägg till ett ärende"/>
     <button class="saveTodo">spara</button>
    </form>
  </div>

  <span class="buttonContainer">
    <button class="sortBtn" @click="() => $emit('sortTodos')">
      sortera a-ö
    </button>
    <button class="clearBtn" @click="() => $emit('clearAll')">
      rensa allt
    </button>
  </span>
</template>
<style scoped>

form {
  display: flex;
  flex-direction: column;
  place-items: center;
  ;
}

.buttonContainer {
  width:80%;
  padding: 1rem;
  border-radius: 10px;
  box-shadow: 0 0 5px 0 rgb(183, 178, 178);
  margin-bottom: 30px;
  background-color: #FFE1EA;
}

.sortBtn,
.clearBtn,
.saveTodo {
  margin-left: 10px;
  margin-right: 10px;
  margin-top: 5px;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  padding: 5px;
  width: 100px;
  background-color: white;
  box-shadow: 0 0 5px 0 rgb(165, 160, 160);
  cursor: pointer;
}

.sortBtn:hover,
.clearBtn:hover {
  background-color: #F1C8DB;
}

.saveTodo:hover {
  background-color: #FFE1EA;
}

.textBox {
  width: 90%;
  border: none;
  border-radius: 10px;
  padding: 5px;
  font-size: 1rem;
  margin: 10px;
  text-align: center;

}

.inputWrapper {
    width:80%;
    padding: 1rem;
    border-radius: 10px;
    box-shadow: 0 0 5px 0 rgb(165, 160, 160);
    margin-bottom: 15px;
    background-color:  #F1C8DB;
  
}

@media screen and (min-width: 768px){

  .inputWrapper {
    width:30%;
}

.buttonContainer {
  width:30%;
}
 
}
</style>
