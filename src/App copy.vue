<script setup>
const name = 'Vue dinamic';
const styleColor = 'color: blue;';
const arrayColors =["blue", "red", "green"];
const activo = true;
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
const arrayFrutas2 = [
        {
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
            stock: 10,
        },
        {
            name: "Pera",
            price: "$2.00",
            description: "Una pera",
            stock: 0,
        },
        {
            name: "Naranja",
            price: "$3.00",
            description: "Una naranja",
            stock: 20,
        },
    ];

var objetoFruta ={
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
            stock: 15,
            id: 1,
        };

</script>

<template>
  <h1> Hola {{ name.toUpperCase() }} js </h1>
  <p></p>
  {{  arrayFrutas }}
  <p></p>
    <ul>
      <li
        v-for="(fruta, index) in arrayFrutas"  
        :key="index"
        >{{ index +1 }}  {{ fruta }}
      </li>
    </ul>

    <p></p>
    
<ul>
  <h2>List 2:</h2>
  <li
        v-for="(fruta, index) in arrayFrutas2"  
        :key="index"
        >{{ index +1 }}.- {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }}
      </li>
</ul>
<p></p>
  <h2>List 3:</h2>
  <p></p>
  {{ objetoFruta }}
  <p></p>
  <li
    v-for="(value, propiedad, index) in objetoFruta"
    :key="index"
  >{{ index +1 }} {{ propiedad }}: {{ value }}
  </li>
<h2>Lista 4:</h2>
<h3>Show only values with stock > 0</h3>
<p></p>
<ul>
  <template v-for="item in arrayFrutas2" :key="item.name">
    <li v-if="item.stock >0">{{ item.name }} - {{ item.price }}</li>

  </template>
</ul>

</template>

<style>
h1{
  color: red;
}
</style>