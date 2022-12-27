<script setup>
import { RouterLink } from "vue-router";

import { useGetData } from "@/composables/getData";

const { data, error, loading, getData } = useGetData();

getData("https://pokeapi.co/api/v2/pokemon");
</script>

<template>
     <h1>Pokemons</h1>
     <p v-if="loading">Cargando...</p>
     <div class="alert alert-danger" v-if="error">Error: {{ error }}</div>
     <div v-if="data">
          <ul class="list-group">
               <li v-for="poke in data.results" class="list-group-item">
                    <router-link :to="`/pokemons/${poke.name}`">{{
                              poke.name
                    }}</router-link>
               </li>
          </ul>
          <div class="my-2">
               <button class="btn btn-outline-danger me-2" @click="getData(data.previous)" :disabled="!data.previous">
                    Previous
               </button>
               <button class="btn btn-outline-primary" @click="getData(data.next)" :disabled="!data.next">
                    Next
               </button>
          </div>
     </div>
</template>