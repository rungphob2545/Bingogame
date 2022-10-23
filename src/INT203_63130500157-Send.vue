<script setup>
import { ref } from 'vue'
const randNumbers = ref([])
const numBing =ref([])
// generates random number in range (1-99)
const generateNumber = () => {
  let duplicate = false
  const rand = Math.floor(Math.random() * 99 + 1)
  duplicate = randNumbers.value.some((randNumber) => randNumber === rand)
  duplicate ? generateNumber() : randNumbers.value.push(rand)
  
}

function reset() {
  document.getElementById("myForm").reset();
}


const addNum = ()=> {
  numBing.value.push(randNumbers.value[randNumbers.value.length -1])
  console.log(numBing.value)
}


const msg ="63130500157 Rungphob Jaraspat"

</script>

<template>
  <div id = "myForm" class="top-container">
   
    <div class="action-button">
      <button @click="generateNumber">Generate New Number</button>
      
      <button @click="reset" >Reset</button>
    </div>
    <div class="error-message">
      <!-- show error message when a user adding the same number in the bingo sheet -->
    </div>
    <div class="grid-container">
      <div class="grid-item">
        <button @click="addNum">Add Number</button>
       <p>{{numBing}}</p>
        
      </div>
      <div class="grid-item">
        <button>Add Number</button>
        
      </div>
      <div class="grid-item">
        <button @click="addNum">Add Number</button>
        
      </div>
      <div class="grid-item">
        <button>Add Number</button>
        
      </div>
      <div class="grid-item">
        <button>Add Number</button>
        
      </div>
      <div class="grid-item">
        <button>Add Number</button>
        
      </div>
      <div class="grid-item">
        <button>Add Number</button>
        
      </div>
      <div class="grid-item">
        <button>Add Number</button>
        
      </div>
      <div class="grid-item">
        <button>Add Number</button>
        
      </div>
      
     
    </div>
    <div class="generate-number">
      <ul>       
           <li v-for="(rand,index) in randNumbers" :key="index">Generate Number #{{index+1}} : '{{rand}}'
           </li>      
      </ul>
      <!-- show the list of generated number here -->
    </div>
  </div>

  {{msg}}
</template>

<style scoped>
.top-container {
  width: 330px;
}
.action-button {
  padding: 10px;
  display: flex;
  gap: 5px;
}
.grid-container {
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 80px 80px 80px;
  column-gap: 5px;
  row-gap: 5px;
  background-color: green;
  padding: 10px;
}
.grid-item {
  display: flex;
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  font-size: 30px;
  text-align: center;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
.generate-number {
  font-size: 20px;
}
.error-message {
  height: 40px;
  color: red;
}
</style>
