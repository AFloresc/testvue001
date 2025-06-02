<script setup>
const name = 'Vue dinamic';

//medtodo - methods
const handleClick = (message) =>{
  console.log(message)
};
</script>

<template>
  <h1> Hola {{ name.toUpperCase() }} js </h1>
  <button v-on:click.right.prevent="handleClick('Texto right')">Activame right</button>
  <button @click.left="handleClick('Texto left')">Activame left</button>
  <button @click.middle="handleClick('Texto Middle')">Activame middle</button>
 </template>

<style>
h1{
  color: red;
}
</style>