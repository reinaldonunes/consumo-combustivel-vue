<script setup lang="ts">
  defineProps<{ copyright: string }>()
</script>

<template>
  <footer class="container-fluid py-3 px-2">
    <div class="container text-center text-white py-5">
      <span class="text-sm text-secondary">{{ copyright }}</span>
    </div>
  </footer>
</template>

<style scoped>
</style>
