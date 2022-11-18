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

const res = await fetch("https://jsonplaceholder.typicode.com/users")
  .then((response) => response.json())
  .then((json) => console.log(json));
console.log(res);
if (!res.ok) {
  throw new Error();
}
response.value = await res.json();
</script>

<template>
  <div>
    <h1>User</h1>
    <p>{{ response.name }}</p>
    <p>{{ response.street }}</p>
  </div>
</template>
