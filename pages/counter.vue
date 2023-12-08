<script setup lang="ts">
  const count = ref(0);
  function addCounter() {
    count.value++;
  }
  function reduceCounter() {
    count.value--;
  }
</script>

<template>
  <h1>Your counter: {{ count }}</h1>
  <button @click="addCounter">+</button>
  <button @click="reduceCounter">-</button>
</template>