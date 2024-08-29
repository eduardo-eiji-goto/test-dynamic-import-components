<script setup>
import Eduardo from "./components/cards/Eduardo.vue";
import John from "./components/cards/John.vue";
</script>

<template>
  <ul id="cards">
    <Eduardo />
    <John />
  </ul>
</template>

<style scoped>
#cards {
  display: grid;
  gap: 1em;
}
</style>
