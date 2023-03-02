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
          form: true,
          loading: false,
          result: false
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
        this.view.form = false
        this.view.loading = true

        let pricePerKm = data.price / data.media
        let totalCost = pricePerKm * data.distance
        let liters = totalCost / data.price

        setTimeout(() => {
          this.view.loading = false
          this.view.result = true
        }, 1000);
       
      },
    }
  })
  
</script>

<template>
  <div class="container px-5">
    <div class="row">
      <div class=" col-9 m-auto bg-custom-violet p-5 rounded-4">
        <FormOptions @calculateCosts="calculateCosts" v-if="view.form" />
        <LoadingProgress v-if="view.loading" />
        <ResultView :result="result" v-if="view.result" />
      </div>
    </div>
  </div>
</template>

<style scoped>
  .bg-custom-violet {
    background: #1c1c26;
  }
</style>
