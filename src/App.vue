<script setup lang="ts">
  import HeaderView from './components/Header.vue'
  //import CalculatorView from './components/Calculator.vue'
  import FooterView from './components/Footer.vue'
</script>

<template>
  <HeaderView v-once />
  <!-- Calculator -->
  <FooterView
    copyright="&copy; 2023 Consumo de combustível por quilometragem - Feito por Reinaldo J.Nunes"
    v-once 
  />
</template>

<style scoped>

</style>
