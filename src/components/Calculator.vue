<script setup lang="ts">
  //defineProps<{ copyright: string }>()
  import FormOptions from './Form.vue'
</script>

<template>
  <div class="container px-5">
    <div class="row">
      <div class=" col-9 m-auto bg-custom-violet p-5 rounded-4">
        <FormOptions />
      </div>
    </div>
  </div>
</template>

<style scoped>
  .bg-custom-violet {
    background: #1c1c26;
  }
</style>
