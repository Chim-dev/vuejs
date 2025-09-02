<template>
  <body class="bg-gray-300">
    <div>
      <span class="text-green-500 font-extrabold flex justify-center" v-html="toUpper()"></span>
    </div>
    <div class="flex flex-col items-center">
      <p>Your Lucky Number is : {{ luckyNumber }}</p>
      <p v-once>your once rendered lucky number is : {{ luckyNumber }}</p>
      <a v-bind:href="blogURL " target="_blank" class="text-red-200 rounded-sm bg-pink-600"> visit blog</a>
      <p>Number available : {{ luckyNumbers }}</p>
      <p>random number {{ getRLN() }}</p>
    </div>
    <br>
    <div class="flex flex-col items-center">
      <p class="text-gray-700 font-extrabold">Your Data : </p>
      <p> Name : {{ employee.name }}</p>
      <p>Age : {{ employee.age }}</p>
      <p>Salary : SGD {{ employee.salary }}</p>
      <p>Time spent in company : {{ employee.yearsWithCompany }}</p>
      <p v-show="employee.hasCorpCard">Spend Limit for Card (show) : {{ employee.spendingLimit }}</p>
      <p v-if="employee.hasCorpCard">Spend Limit for Card (if) : {{ employee.spendingLimit }}</p>
      <p v-else-if="employee.salary > 2500 && employee.yearsWithCompany>1">Employee is eligible for a corp Card</p>
      <p v-else>Employee doesn't meet a minimum requirements for a corporate card</p>
    </div>
  </body>
</template>

<script setup>
import { reactive, ref } from 'vue';
  const newMsg = 'Hello vue.js';
  let luckyNumber = ref(7);
  const luckyNumbers = [3,2,1,4,1,21,3,3]
  const employee = reactive ({
    name: "Jane Doe",
    age: 20,
    salary: 2600,
    hasCorpCard: false,
    spendingLimit: 20000,
    yearsWithCompany: 2,
  })
  const blogURL = "https://komiku.org/manga/spy-x-family/"
  function getRLN(){
    setTimeout(() => {
      luckyNumber.value = Math.floor(Math.random()*10) + 1;
      employee.salary = 1000;
    }, 1000);
    
  }
  
  function toUpper() {
    return '<h1><u>newMsg</u></h1>';
  }
  
</script>