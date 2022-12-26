<script setup>
import axios from 'axios';
import { ref } from 'vue';
import { RouterLink } from 'vue-router';
const pokemons = ref([]);

const getData = async () => {
     try {
          const { data } = await axios.get('https://pokeapi.co/api/v2/pokemon/');
          pokemons.value = data.results;
     } catch (error) {
          console.log(error);
         
     }
};
getData();
</script>




<template>
     <h1>Pokemons</h1>
     <ul>
          <li v-for="poke in pokemons">
               <RouterLink :to="`/pokemons/${poke.name}`"> {{ poke.name }}</RouterLink>

          </li>
     </ul>
</template>