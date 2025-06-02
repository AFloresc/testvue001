<script setup>
import {ref} from 'vue'

const name = 'Vue dinamic';

let counter = 0;

//Contador reactivo
const counterN = ref(0);

const increment=()=>{
  
  counterN.value ++;
  
}

</script>

<template>
  <h1> Hola {{ name.toUpperCase() }} js </h1>
  <h2>{{ counterN }}</h2>
  <button @click="increment">Aumentar</button>
 
 </template>

<style>
h1{
  color: red;
}
</style>