<script setup>
import task from './task.vue';
import { ref } from 'vue';


const tasks = ref([]);
const taskName = ref('');


const addTask = () => {
  const newTask = taskName.value.trim();
  if (newTask !== '') {
    tasks.value.push({task : newTask, isCheck : false,  isReadOnly : ref(true), isChecked : ref(false)})
    taskName.value = '';
  }
}

const clearAll = () =>{
    tasks.value = [];
}


</script>

<template>
    <main class="container">
        <h2 class="head">save your daily tasks here !</h2>
        <div class="inputCont">
            <input class="input" @keydown.enter="addTask" v-model="taskName" placeholder="Name your next task!">
            <p class="button" @click="addTask">Add</p>
        </div>
        
        <task :tasks="tasks"/>
        <footer>
            <p>you have 5 tasks in total</p>
            <p class="clearAll" @click="clearAll">Clear All</p>
        </footer>
    </main>
</template>

<style scoped>

.container{
    overflow-y :scroll;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    width: 40%;
    min-height: 200px;
    max-height: 550px;
    text-align: left;
    padding-left: 33px;
    border-radius: 10px;
  }
  
  .head{
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    font-size: 30px;
    margin-bottom: 7px;
  }
  
  .inputCont{
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .input{
    padding-left: 10px;
    margin-right: 10px;
    height: 40px;
    width: 70%;
    border: 1px solid #ccc;
  }
  
  .input:hover{
    border: none;
  }
  
  .button{
    margin-right: 15px;
    background-color: #8D49E7;
    height: 33px;
    width: 50px;
    color: white;
    font-size: 20px;
    padding-top: 7px;
    padding-bottom: 3px;
    text-align: center;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    border-radius: 5px;
    transition:  0.3s ease;
  }
  
  .button:hover{
    cursor: pointer;
    background-color: #af85e6;
  }
  
  footer{
    display: flex;
    justify-content: space-between;
    width: 90%;
    margin-bottom: 10px;
  }
  
  footer p{
    font-weight: bold;
  }
  
  .clearAll{
    background-color: #8D49E7;
    height: 26px;
    width: 70px;
    color: white;
    font-size: 13px;
    padding-top: 12px;
    text-align: center;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    border-radius: 5px;
    transition:  0.3s ease;
  }
  
  .clearAll:hover{
    cursor: pointer;
    background-color: #af85e6;
  }

</style>
