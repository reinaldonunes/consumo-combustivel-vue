<script lang="ts">
  import FormOptions from './Form.vue'
  import LoadingProgress from './Loading.vue'
  import ResultView from './Result.vue'

  import { defineComponent } from 'vue'

  interface DataOptions{
    distance: number
    media: number
    price: number
  }

  export default defineComponent({
    components: {
      FormOptions,
      LoadingProgress,
      ResultView
    },
    data(){
      return{
        view: {
          stage: 0
        },

        result: {
          active: false,
          priceKm: 0,
          totalCalc: 0,
          litersCar: 0
        }
      }
    },
    methods: {
      calculateCosts(data: DataOptions){
        this.view.stage++
        
        setTimeout(() => {
          this.result.priceKm = data.price / data.media
          this.result.totalCalc = this.result.priceKm * data.distance
          this.result.litersCar = this.result.totalCalc / data.price
          this.result.active = true
          
          this.view.stage = 0
        }, 1000);
      }
    }
  })
  
</script>

<template>
  <div class="container">
    <div class="row rounded-4 bg-custom-violet justify-content-between">
      <div class="col-6 d-flex align-items-center">
        <FormOptions @calculateCosts="calculateCosts" v-if="view.stage === 0" />
        <LoadingProgress v-if="view.stage === 1" />
      </div>
      <div class="col-6">
        <ResultView :result="result"/>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .bg-custom-violet {
    background: #1c1c26;
  }
</style>
