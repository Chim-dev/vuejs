<!-- <template>
  <body class="bg-gray-300">
    <div>
      <span class="text-green-500 font-extrabold flex justify-center" v-html="toUpper()"></span>
    </div>
    <div class="flex flex-col items-center">
      <p>Your Lucky Number is : {{ luckyNumber }}</p>
      <p v-once>your once rendered lucky number is : {{ luckyNumber }}</p>
      <a v-bind:href="blogURL " target="_blank" class="text-red-200 rounded-sm bg-pink-600"> visit blog</a>
      <p>Number available : {{ luckyNumbers }}</p>
      Lucky Number :
      <span v-for="(luckyNumber,index) in luckyNumbers">{{ luckyNumber }}</span>
      <hr>

      <p>Project in progress menuju indonesia cemas 2045</p>
      <ul>
        <li v-for="(liga_korupsi, index) in employee.ligaKorupsi">
          <span>No : {{ index+1 }} - {{ liga_korupsi.project }} - Timeline {{ liga_korupsi.timeline }}</span>
        </li>
      </ul>
      <br>

      <ul>
        <li v-for="(key,value) in employee">
          <span>{{ value }} : {{ key }}</span>
        </li>
      </ul>
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
    salary: 2100,
    hasCorpCard: false,
    spendingLimit: 20000,
    yearsWithCompany: 2,
    ligaKorupsi: [
      {project: "Korupsi emas", timeline: "selama owo menjabat"},
      {project: "Korupsi pertamina", timeline: "selama owo menjabat"},
      {project: "Korupsi bank indonesia", timeline: "selama owo menjabat"},
      {project: "Korupsi dinasti", timeline: "selama owo menjabat"},
    ]
  })
  const blogURL = "https://komiku.org/manga/spy-x-family/"

  function getRLN(){
    setTimeout(() => {
      luckyNumber.value = Math.floor(Math.random()*10) + 1;
      employee.salary = 4000;
    }, 1000);
    
  }
  
  function toUpper() {
    return '<h1><u>newMsg</u></h1>';
  }
  
</script> -->


<template>
  <div class="bg-gray-300 min-h-screen p-5">
    <div>
      <span class="text-green-500 font-extrabold flex justify-center" v-html="toUpper()"></span>
    </div>

    <div class="flex flex-col items-center">
      <p>Your Lucky Number is : {{ luckyNumber }}</p>
      <p v-once>Your once rendered lucky number is : {{ luckyNumber }}</p>

      <a :href="blogURL" target="_blank" class="text-red-200 rounded-sm bg-pink-600 px-2 py-1 mt-2">
        Visit Blog
      </a>

      <p class="mt-3">Number available : {{ luckyNumbers }}</p>
      Lucky Numbers:
      <span v-for="(num, index) in luckyNumbers" :key="index" class="mx-1">{{ num }}</span>

      <button @click="getRLN" class="bg-blue-500 text-white px-3 py-1 rounded mt-3">
        Generate Lucky Number
      </button>

      <hr class="my-4 w-full border-gray-500">

      <p class="font-bold">Project in progress menuju Indonesia cemas 2045</p>
      <ul>
        <li v-for="(liga, index) in employee.ligaKorupsi" :key="index">
          <span>No : {{ index+1 }} - {{ liga.project }} - Timeline {{ liga.timeline }}</span>
          <input type="text"/>
        </li>
      </ul>
      {{ shuffleEmployeeProject() }}

      <br>
      <ul>
        <li v-for="(value, key) in employee" :key="key">
          <span>{{ key }} : {{ value }}</span>
        </li>
      </ul>
    </div>

    <div class="flex flex-col items-center mt-5">
      <p class="text-gray-700 font-extrabold">Your Data : </p>
      <p>Name : {{ employee.name }}</p>
      <p>Age : {{ employee.age }}</p>
      <p>Salary : SGD {{ employee.salary }}</p>
      <p>Time spent in company : {{ employee.yearsWithCompany }}</p>
      <p v-show="employee.hasCorpCard">Spend Limit (show): {{ employee.spendingLimit }}</p>
      <p v-if="employee.hasCorpCard">Spend Limit (if): {{ employee.spendingLimit }}</p>
      <p v-else-if="employee.salary > 2500 && employee.yearsWithCompany > 1">Eligible for Corp Card</p>
      <p v-else>Not eligible for Corp Card</p>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue';

const newMsg = 'Hello vue.js';
let luckyNumber = ref(7);
const luckyNumbers = [3, 2, 1, 4, 1, 21, 3, 3];

const employee = reactive({
  name: "Jane Doe",
  age: 20,
  salary: 2100,
  hasCorpCard: false,
  spendingLimit: 20000,
  yearsWithCompany: 2,
  ligaKorupsi: [
    { project: "Korupsi emas", timeline: "selama owo menjabat" },
    { project: "Korupsi pertamina", timeline: "selama owo menjabat" },
    { project: "Korupsi bank indonesia", timeline: "selama owo menjabat" },
    { project: "Korupsi dinasti", timeline: "selama owo menjabat" },
  ]
})

const blogURL = "https://komiku.org/manga/spy-x-family/"

function getRLN() {
  setTimeout(() => {
    luckyNumber.value = Math.floor(Math.random() * 10) + 1;
    employee.salary = 4000;
  }, 1000);
}

function toUpper() {
  return `<h1><u>${newMsg.toUpperCase()}</u></h1>`;
}

function shuffleEmployeeProject() {
  setTimeout(() => {
    employee.ligaKorupsi.sort(() => Math.random()-0.5);
  },5000);
}
</script>
