<script setup>
  import { page } from '../store.js';

  window.addEventListener('hashchange', () => {
    page.value = window.location.hash.substring(1);
  });

  page.value = window.location.hash.substring(1) || 'home';

</script>

<template>
  <nav>
    <ul>
      <li>
        <a href="#home">Home</a>
      </li>
      <li>
        <a href="#temperature">Temperatures</a>
      </li>
      <li>
        <a href="#data-storage">Data storage</a>
      </li>
    </ul>
  </nav>
</template>

<style scoped>

</style>