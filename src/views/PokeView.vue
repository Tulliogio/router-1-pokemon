<script setup>
import { useRoute, useRouter } from "vue-router";
import { useGetData } from "@/composables/getData";
import { useFavoritoStore } from "@/store/favoritos";
const route = useRoute();
const router = useRouter();
const useFavorito = useFavoritoStore();

const back = () => {
     router.push("/pokemons");
};
const { add, findPoke } = useFavorito;
const { data, error, loading, getData } = useGetData();

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
</script>

<template>
     <div v-if="loading">Cargando...</div>
     <div v-else>
          <div v-if="data">
               <img :src="data.sprites?.front_default" alt="" />
               <h1>Poke name: {{ $route.params.name }}</h1>
               <button class="btn btn-outline-primary mb-2" :disabled="findPoke(data.name)" @click="add(data)">
                    Agregar Favorito
               </button>
          </div>
          <h1 v-if="error">No existe el pokemon</h1>
          <button @click="back" class="btn btn-outline-primary">Volver</button>
     </div>
</template>