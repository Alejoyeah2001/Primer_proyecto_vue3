<script setup>

import{ref, computed} from 'vue'

const arrayNumeros = ref([]);

const name = "Hola mi amorr, MUA MUA <3"

//metodo - methodsS

const handleClick = (message) =>{
  console.log(message)
}
//en javascript vanilla el const es un poco mejor para la renderización
const counter = ref(0);

const increment =() =>{
  console.log('aumentar contador')
  counter.value  ++;
  


}
//reducir el contador
const descreace =() =>{
  console.log('disminuir contador')
  counter.value  --;


}
//Vuelva a 0
const reset =() =>{
  console.log('resetear contador')
  counter.value  =0;


}


const classCounter = computed(() => {

  if(counter.value === 0 ){
    return 'zero'
  }
  if(counter.value > 0){
    return 'positive'
  }
  if(counter.value < 0){
    return 'negative'
  }
});

//agregar a un array

const agregar =() =>{
  arrayNumeros.value.push(counter.value)
}

const bloquearBtnAdd= computed(() => {
  const numSearch = arrayNumeros.value.find(num => num === counter.value)
  //console.log(numSearch)
  //el 0 siempre lo interpreta como false
  if(numSearch===0) return true;  
  return numSearch ? true : false;
})

</script>

<template>
  <div class="container">
    <h1>Hola {{ name.toUpperCase() }}</h1>

    

<!-- prevent es para omitir la función predeterminada -->
<!--
  <p>
<div class="btn-group">
  <button v-on:click.right.prevent="handleClick('Texto right')" >Activame right</button>
  <button @click.left="handleClick('Texto left')" >Activame left</button>
  <button @click.middle="handleClick('Texto middle')" >Activame middle</button>


</div>
  
</p>-->

<p>

  <!-- Si el contador es menor a 0 aparece en rojo, caso contrario verde  -->
  <!-- <h1>Parte dos</h1> -->
<h2 :class="classCounter"> {{ counter }} </h2>
<div class="btn-group">
  <button @click="increment" class="btn btn-success">Aumentar</button>
<button @click="descreace" class="btn btn-danger">disminuir</button>

<button @click="reset" class="btn btn-secondary">resetear</button>
<button @click="agregar" :disabled="bloquearBtnAdd" class="btn btn-primary">ADD </button>


</div>

</p>
<p>
<!-- ir agregando números en un array -->
  {{ arrayNumeros }}
  <!-- Forma de lista -->

<ul class="list-group">
  <li class="list-group-item" v-for = "(num, index) in arrayNumeros" :key="index">
     {{ num }}
    </li>

</ul>
      
</p>

  


  </div>
    




</template>




<style>

h1{
  color: red;
  font: 100;
}
.positive{
  color: green;
}
.negative{
  color: red;
}
.zero{
  color: peru;
}

</style>