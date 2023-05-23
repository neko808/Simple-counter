<script setup>
  import {ref, computed } from 'vue';
 

  const name = 'Dynamic Vue';
  const numArray = ref([]);

  let counter = ref(0);

  const increment = () => counter.value++;

  const decrement = () => counter.value--;

  const reset = () => (counter.value) = 0;
  
  const classCounter = computed(() => {
    if(counter.value === 0){
      return 'zero'
    }
    if(counter.value > 0){
      return 'positive'
    }
    if(counter.value < 0){
      return 'negative'
    }
  });

  const addNum = () => {
    numArray.value.push(counter.value);
  }

  const bloquearBtn = () => {
     const numSearch = numArray.value.find( num => num === counter.value)
     console.log(numSearch);
     if(numSearch === 0){ return true };
     return numSearch ? true : false;

    //  return numSearch || numSearch === 0;
    
  }
    
</script>
  

<template>

  <h1>Hola {{ name.toLocaleUpperCase() }}</h1>

  <h2 :class="classCounter">{{ counter }}</h2>

  <button @click="increment()">Aumentar</button>
  <button @click="decrement()">Disminuir</button>
  <button @click="reset()">Reset</button>
  <button @click="addNum()" :disabled=bloquearBtn()>Add</button>
  <ul>
    <li v-for="(num, index) in numArray" :key="index">{{ num }}</li>
  </ul>
 

</template>

<style>
.positive{
  color: green
}
.negative{
  color: red
}
.zero{
  color: peru;
}

</style>
 

  