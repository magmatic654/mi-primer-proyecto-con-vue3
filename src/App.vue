  <script setup>
  import { ref, computed } from "vue";
  
  const name = 'Vue dinamico';
  
  const counter = ref(0);
  
  
  const increment = ()=> counter.value++;
  
  const decrement = ()=> counter.value--;
  
  const reset = ()=> {
    arrayFavoritos.value = []
    counter.value = 0;}
  
  
  const classCounter = computed(()=>{
    if(counter.value === 0){
      return 'zero'
    }else if(counter.value > 0){
      return 'positive'
    }else{
      return 'negative'
    }
  })

  const arrayFavoritos = ref([])

  const numberExist = computed(()=>{
    const numExiste = arrayFavoritos.value.includes(counter.value)
    return numExiste
  })

  const addNumber = ()=>{
      arrayFavoritos.value.push(counter.value)
  }




  </script>

<template>
  <div class="container text-center mt-3">
    <h2 :class="classCounter" >{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="decrement" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-warning">Resetear</button>
      <button @click="addNumber" class="btn btn-primary" :disabled="numberExist">Agregar</button>
    </div>
    <ul class="list-group mt-3">
        <li class="list-group-item" v-for="elemento in arrayFavoritos">
          {{ elemento }}
        </li>
    </ul>
  </div>
</template>

<style>

  .positive{
    color: green
  }
  .negative{
    color: red;
  }
  .zero{
    color:black;
  }
  </style>