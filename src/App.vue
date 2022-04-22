<script setup>
  import { computed } from '@vue/runtime-core';
  import AppConverter from './components/AppConverter.vue';
  import TheNav from './components/TheNav.vue';
  import { page } from './store.js';

  const convertersConfig = {
    'temperature': {
      title: 'Temperature',
      decimalPlaces: 2,
      units: [
        {
          label: 'Kelvin', symbol: 'K',
          get: val => val,
          set: val => val
        }, {
          label: 'Celsius', symbol: '°C',
          get: val => val + 273.15,
          set: val => val - 273.15
        }, {
          label: 'Fahrenheit', symbol: '°F',
          get: val => val * 1.8 - 459.67,
          set: val => (val + 459.67) / 1.8
        }
      ]
    },
    'data-storage': {
      title: 'Data storage',
      decimalPlaces: 12,
      units: [
        {
          label: 'Byte', symbol: 'B',
          get: val => val,
          set: val => val
        }, {
          label: 'Megabyte', symbol: 'MB',
          get: val => val / 1e+6,
          set: val => val * 1e+6
        }, {
          label: 'Gigabyte', symbol: 'GB',
          get: val => val / 1e+9,
          set: val => val * 1e+9
        }, {
          label: 'Terabyte', symbol: 'TB',
          get: val => val / 1e+12,
          set: val => val * 1e+12
        }
      ]
    }
  };

</script>

<template>

  <the-nav></the-nav>

  <template v-if="page == 'home'">
    <h1>Welcome to the converter app</h1>
  </template>

  <template v-for="(conf, key) in convertersConfig" :key="key">
    <app-converter
      v-if="key == page"
      :units="conf.units"
      :decimalPlaces="conf.decimalPlaces"
      :title="conf.title"
    />
  </template>

</template>

<style>
  * {
    box-sizing: border-box;
  }
</style>
