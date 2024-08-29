<template>
  <article class="card">
    <h1>Hi, I'm {{ name }}</h1>
    <button @click="updateName">Do not click!</button>
  </article>
</template>

<script setup lang="js">
import { ref } from 'vue';

const name = ref("Eduardo")

function updateName() {
    name.value = "ur mom! owo"
}
</script>

<style lang="css" scoped>
.card {
  padding: 3rem;
  border: 1px solid white;
  border-radius: 1rem;

  position: relative;
}

.card::after {
  content: "";
  display: inline-block;

  width: 6rem;
  aspect-ratio: 1;

  background-image: url(/vite.svg);
  background-size: cover;

  position: absolute;
  top: 0;
  right: 0;
  transform: translate(30%, -30%) rotate(15deg);
}
</style>
