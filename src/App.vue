<script setup>
import {ref, computed} from 'vue'

const name = 'Vue dinamic';

let counter = 0;

//Contador reactivo
const counterN = ref(0);

//Array de numeros
const arrayNumeros = ref([]);

const increment=()=>{
  counterN.value ++;
};

const decrement =()=>{
  if (counterN.value > 0) {
    counterN.value--;
  }
  else {
    counterN.value = 0;
  }
};

const reset =()=>{
  counterN.value = 0;
};

// Add number to a list
const addNumber =()=>{
  arrayNumeros.value.push(counterN.value)
  console.log(arrayNumeros)

};

const getColor = (counterN) =>{
  if (counterN > 0) {
          return "green";
        } else {
          if (counterN==0) {
            return "black"
          } else {
            return "red"
          }
}
}




// Se recomuenda usar el computed con datos reactivos por el uso de la cache
const classCounter = computed(()=>{
  if(counterN.value===0 ){
    return "black"
  }
  if(counterN.value>0){
    return "green"
  }
  return "red"
})


const checkArray=() =>{
  if (arrayNumeros.includes(counterN.value)){
    console.log(true)
    return true
  }
  console.log(false)
  return false
}

const bloquearBtnAdd = computed(()=>{
  const numSearch = arrayNumeros.value.find(num => num===counterN.value)
  //console.log(numSearch)
  //if (numSearch ===0) return true
  //return numSearch ? true : false;
  return numSearch || numSearch ===0;
});

</script>

<script>
export default {
  methods: {
    changeColor(counterN) {
      try {
        if (counterN > 0) {
          return "green";
        } else {
          if (counterN==0) {
            return "black"
          } else {
            return "red"
          }
        } 
      } catch (error) {
        return "black";
      }
    }
  }
};


</script>

<template>
  <div class="container text-center mt-3">
    <h1> Test {{ name.toUpperCase() }} js </h1>
  <!-- Other ways-->
  <!-- <h2 :class="counterN > 0  ? 'green' : 'red'"> {{ counterN }}</h2> 
  <h2 :class="getColor(counterN)"> {{ counterN }}</h2>-->
  <h2 :class="classCounter"> {{ counterN }}</h2>
  <div class="btn-group">
    <button @click="increment" class="btn btn-success">Increment</button>
    <button @click="decrement" class="btn btn-danger">Decrement</button>
    <button @click="reset" class="btn btn-secondary">Reset</button>
    <button @click="addNumber" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button>
    
  </div>

  
  <ul class="list-group mt-4">
    <li 
      class="list-group-item"
      v-for="(num, index) in arrayNumeros" 
      :key="index"
    >
    {{ num }}

    </li>
  </ul>
  </div>
  
 </template>

<style>
h1{
  color: red;
}

.red{
  color: red;
}

.green{
  color:green;
}

.black{
  color:black
}
</style>