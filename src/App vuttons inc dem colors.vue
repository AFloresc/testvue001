<script setup>
import {ref} from 'vue'

const name = 'Vue dinamic';

let counter = 0;

//Contador reactivo
const counterN = ref(0);

const increment=()=>{
  
  counterN.value ++;
  
}

const decrement =()=>{
  if (counterN.value > 0) {
    counterN.value--;
  }
  else {
    counterN.value = 0;
  }
}

const reset =()=>{
  counterN.value = 0;
}


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
  <h1> Hola {{ name.toUpperCase() }} js </h1>
  
  <h2 :class="changeColor(counterN)"> {{ counterN }}</h2>
  
  <button @click="increment">Aumentar</button>
  <button @click="decrement">Disminuir</button>
  <button @click="reset">Reset</button>
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