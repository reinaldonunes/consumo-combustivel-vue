<script setup lang="ts">
</script>

<template>
  <div class="text-center">
    <span class="lead text-secondary m-auto d-block text-center mb-3">Aguarde, efetuando cálculo.</span>
    <div class="progress">
      <div class="progress-bar" role="progressbar" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100"></div>
    </div>
  </div>
</template>

<style scoped>
  .progress-bar{
    background-color: #03bd70;
    animation: animateProgress 1s ease-in;
    animation-fill-mode: forwards;
  }

  @keyframes animateProgress {
    0% { width:0%}
    100% { width: 100%; }
  }
</style>
