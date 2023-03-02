<script lang="ts">
  import { defineComponent } from 'vue'

  export default defineComponent({
    data(){
      return{
        form: {
          distance: null,
          media: null,
          price: null,
        }
      }
    },
    
    methods: {
      validateForm(){
        if(!this.form.distance){
          alert("Preencha o campo Distância total!")
          return
        }
        if (!this.form.media) {
          alert("Preencha o campo Média do veículo!")
          return
        }
        if (!this.form.price) {
          alert("Preencha o campo Preço do combustível!")
          return
        }
    
        this.$emit('calculateCosts', this.form)
      }
    }
  })
</script>

<template>
  <Transition >
    <form>
      <div class="mb-4">
        <label
          form="distance" 
          class="form-label lead text-white">Distância total (km)</label>
        <input
          type="text" 
          id="distance" 
          v-model="form.distance" 
          class="form-control py-3 px-3" 
          placeholder="Ex. 55" aria-label="true" />
      </div>

      <div class="mb-4">
          <label
            form="media" 
            class="form-label lead text-white">Média do veículo (km/l)</label>
          <input
            type="text" 
            id="media" 
            v-model="form.media" 
            class="form-control py-3 px-3" 
            placeholder="Ex. 4.3" aria-label="true" />
        </div>

        <div class="mb-4">
          <label
            form="price" 
            class="form-label lead text-white">Preço do combustível (R$/l)</label>
          <input
            type="text" 
            id="price" 
            v-model="form.price" 
            class="form-control py-3 px-3" 
            placeholder="Ex. 3.25" aria-label="true" />
        </div>
        <div>
          <button
            type="button"
            class="btn btn-primary fw-bold w-100 py-3 px-5"
            @click="validateForm"
          >GERAR RESULTADOS</button>
        </div>
        
    </form>
  </Transition>
</template>

<style scoped>
  .btn-primary{
    background:#4b3b72;
    border:1px solid #7a6c9e;
    border-bottom:4px solid #7a6c9e;

    font-size:20px;
  }
  .btn-primary:hover{
    border: 1px solid #03bd70;
    border-bottom-color: rgb(3, 189, 112);
    border-bottom-style: solid;
    border-bottom-width: 1px;
    border-bottom: 4px solid #03bd70;
    background: #119f64;
  }
</style>