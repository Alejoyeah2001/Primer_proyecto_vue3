<script setup>


const name="Hola vue en variable"
const stylecolor = "color: blue"
const arrayColores = ["blue","red","peru"]
const activo = true
//const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
const objetoFrutas = {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,

}
const arrayFrutas = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];

</script>

<template>
  
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <p></p>
  <h2>{{ arrayColores }}</h2>
  <p></p>
  <!--v-bind es para colocar con un const el estilo-->
  <!--Para usar jS es poner el signo `` con ALT + 96, eso permitirá llamar un array usando JS-->
  <h2 :style="`color: ${arrayColores[2]}`"> Soy azul</h2>
  <!--un if y else-->
  <p></p>
  <h2>{{ activo ? 'Estoy Activo' : 'Estoy inactivo'}}</h2>
<p></p>
  
  <!-- v-if  , funciona directamente con el dom. Si no cumple no sale en los elementos.-->
  <p v-if="!activo" >Estoy inactivo</p>
  <p v-else-if="activo"> Estoy activo</p>
  <p v-else> Estoy indeciso</p>

  <h2 v-show="activo"><p>Estoy activo v-show</p></h2>

  <!--v-for  es importante definir un key que es el identificador unico-->
  <ul>

    <!--    un array simple
      <li  v-for = "(fruta, index) in arrayFrutas" :key="index">
     {{index}} - {{ fruta }}
    </li>-->

    <!-- un array complejo
      crear un array fruta para el for, como una variable estandar del for -->
    <!--<li v-for = "(fruta) in arrayFrutas" :key ="fruta.name">
      {{fruta.name}} - {{ fruta.description }} - {{ fruta.price }}

    </li>-->


    <li v-for="(value, propiedad, index) in objetoFrutas" :key="value">
      {{ index }} - {{ propiedad }} : {{ value }}
    </li>
  </ul>

<p>
  ---------------------------
</p>
<!-- v-if tiene mayor peso que el v-for -->
<!-- combinar v-if con v-for usando template -->
<ul>
  <template v-for="item in arrayFrutas"
  :key="item.name"  >
  <li v-if="item.stock > 0">
  {{ item.name }} - {{ item.price }}
</li>
  </template>

  

  



</ul>


</template>


<style>
h1{
  color: red;
}
</style>