<script lang="ts">
  import { defineComponent } from 'vue'

  export default defineComponent({
    props: {
      result: Object
    }
  })
</script>

<template>
  <div class="text-center">
    <div class="d-grid gap-2 mb-3">
      <span class="lead text-white text-center">Seu veículo gasta (R$/km)</span>
      <span class="h4 text-secondary text-center">R$ {{ result?.priceKm }}</span>
    </div>

    <div class="d-grid gap-2 mb-3">
      <span class="h4 fw-bold text-white text-center">TOTAL DESLOCAMENTO</span>
      <span class="h4 text-custom-green text-center">R$ {{  result?.totalCalc }}</span>
      <span class="h6 text-custom-violet text-center">ou {{ result?.litersCar }} litro(s).</span>
    </div>
  </div>
</template>

<style scoped>
  .text-custom-green {
    color: #25d88d;
}
.text-custom-violet{
  color:#4b3b72;
}
</style>