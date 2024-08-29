<script setup>
import { defineAsyncComponent, shallowRef } from "vue";

let cards = shallowRef([]);

// Importing all .vue files from the cards folder
Object.keys(import.meta.glob("./components/cards/*.vue", { eager: true }))
  // We receive the whole path as a variable, which isn´t allowed to be passed on to import()
  // https://github.com/rollup/plugins/tree/master/packages/dynamic-import-vars#limitations
  // Split the component path on / and .
  // Get penultimate (file's name)
  .map((card) => {
    return card.split(/[\/ .]/).slice(-2)[0];
  })
  .forEach((card) => {
    cards.value.push(
      // Import Async Component
      defineAsyncComponent(() => import(`./components/cards/${card}.vue`))
    );
  });
</script>

<template>
  <ul id="cards">
    <component v-for="card in cards" :key="card" :is="card"></component>
  </ul>
</template>

<style scoped>
#cards {
  display: grid;
  gap: 1em;
}
</style>
