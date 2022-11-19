<script setup>
import { ref, onErrorCaptured } from "vue";
const response = ref({});

// adding delay

await new Promise((resolve) => {
  setTimeout(() => {
    resolve();
  }, 1000);
});

onErrorCaptured((err) => {
  // error processing
});

response.value = await (
  await fetch("https://jsonplaceholder.typicode.com/users/1")
).json();
</script>

<template>
  <div>
    <h1>User</h1>
    <p>{{ response.name }}</p>
    <p>{{ response.street }}</p>
  </div>
</template>
