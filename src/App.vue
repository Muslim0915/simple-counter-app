<template>
  <div class="app">
    <CounterList />
  </div>
</template>

<script setup lang="ts">

import CounterList from "@/components/CounterList.vue";
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%;
  height: 100%;
  padding: 2rem;
  font-family: sans-serif;
}
</style>
