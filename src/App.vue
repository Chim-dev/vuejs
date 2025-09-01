<template>
  <h1 class="text-green-500 font-extrabold">{{ toUpper() }}</h1>
  <p>Your Lucky Number is : {{ luckyNumber }}</p>
  <p>Number available : {{ luckyNumbers }}</p>
  <p>random number {{ getRLN() }}</p>
  <br>
  <div class="bg-black-600">
    <p class="text-gray-700 font-extrabold">Your Data : </p>
    <p> Name : {{ employee.name }}</p>
    <p>Age : {{ employee.age }}</p>
    <p>Salary : SGD {{ employee.salary }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';
  const newMsg = 'Hello vue.js';
  let luckyNumber = ref(7);
  const luckyNumbers = [3,2,1,4,1,21,3,3]
  const employee = {
    name: "Jane Doe",
    age: 20,
    salary: 4500,
  }

  function getRLN(){
    setTimeout(() => {
      luckyNumber.value = Math.floor(Math.random()*10) + 1;
    }, 2000);
    
  }
  
  function toUpper() {
    return newMsg.toUpperCase();

  }
  
</script>