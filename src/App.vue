<script setup>

import { ref } from 'vue';
const pops=ref(0)
const list=ref({
  name:'',
  clock:''
})
const taskList =ref([  
])
const make_task =()=>{
pops.value++
}

const save_task=()=>{
  
  taskList.value.push({task_name:list.value.name, time: list.value.clock})
 
  list.value.name=''
  list.value.clock=''
  pops.value=0

}
const remove_task=()=>{
  taskList.value.pop()
}
</script>

<template>
  <div class="main">
    <table class="table">
  <tr class="tr">
  <th>Task Name</th>
  <th>Time</th>
  <th>Action</th>

  </tr>

  <tr v-for="task,index in taskList " :key="index">
    <td>{{task.task_name}}</td>
    <td>{{task.time}}</td>
    <td><button @click="remove_task()">Remove</button></td>
  </tr>
  
 
</table>
  </div>



<div v-show="1==pops" >
  Task name : <input type="text"  v-model="list.name">
   Time : <input type="text" v-model="list.clock">
    <button @click="save_task()">Save</button>
</div>



<button @click="make_task()" class="but">Add Task</button>



</template>

<style scoped>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
  margin-bottom: 20px;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}

</style>