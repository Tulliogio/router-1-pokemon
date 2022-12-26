<script setup>
import { RouterLink, RouterView } from 'vue-router';


</script>

<template>
  <nav class="navbar bg-body-tertiary">
    <div class="container">


      <RouterLink class="navbar-brand" to="/">
        <img src="@/assets/logo.svg" alt="Bootstrap" width="30" height="24"
          class="d-inline-block align-text-top">PokeApi
      </RouterLink>
      <div>
        <RouterLink to="/" class="btn btn-outline-primary me-2 ">Home</RouterLink>
        <RouterLink to="/pokemons" class="btn btn-outline-primary ">Pokemons</RouterLink>
      </div>
    </div>
  </nav>

  <div class="container">
    <RouterView />
  </div>
</template>


