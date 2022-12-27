<script setup>
import { useCounterStore } from "@/store/counter";
const useCounter = useCounterStore();
</script>

<template>
  <h1>Home Counter: {{ useCounter.count }}</h1>
  <h2>Double: {{ useCounter.double }}</h2>
  <button @click="useCounter.increment">Increment</button>
</template>
