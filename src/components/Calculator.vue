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
          priceKm: 0,
          totalCalc: 0,
          litersCar: 0
        }
      }
    },
    methods: {
      calculateCosts(data: DataOptions){
        this.view.stage++

        this.result.priceKm = data.price / data.media
        this.result.totalCalc = this.result.priceKm * data.distance
        this.result.litersCar= this.result.totalCalc / data.price

        setTimeout(() => {
          this.view.stage++
        }, 1000);
       
      },

      resetSteps(){
        this.view.stage = 0
      }
    }
  })
  
</script>

<template>
  <div class="container px-5">
    <div class="row">
      <div class=" col-9 m-auto bg-custom-violet p-5 rounded-4">
        <FormOptions @calculateCosts="calculateCosts" v-if="view.stage === 0" />
        <LoadingProgress v-if="view.stage === 1" />
        <ResultView :result="result" v-if="view.stage === 2" @resetSteps="resetSteps" />
      </div>
    </div>
  </div>
</template>

<style scoped>
  .bg-custom-violet {
    background: #1c1c26;
  }
</style>
