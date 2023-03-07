<script lang="ts">
  import { defineComponent } from 'vue'

  export default defineComponent({
    props: {
      result: Object
    },

    methods:{
      returnStage(){
        this.$emit('resetSteps')
      }
    }
  })
</script>

<template>
  <div class="p-5 align-items-center d-flex w-100 h-100">
    <div class="text-center bg-dark p-5 w-100 rounded-4" v-if="result?.active">
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
    <div class="text-center p-5" v-else>
      <figure class="m-auto overflow-hidden" style="height:374px">
        <p class="text-secondary h4 fw-light mt-4">Insira os dados no formulário ao lado.</p>
        <img src="/waiting.png" alt="Aguardando.." title="Aguardando.." class="img-fluid" style="margin-top:-70px"/>
      </figure>
    </div>
  </div>
</template>

<style scoped>
  .text-custom-green {
    color: #25d88d;
}
.text-custom-violet{
  color:#7151c1;
}
</style>