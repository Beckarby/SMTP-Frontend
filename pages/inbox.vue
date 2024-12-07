<template>
  <div class="homepage bg-gray-100 p-5">
    <h2 class="title text-gray-800 text-2xl font-bold">
      Welcome to the homepage
    </h2>
    <Button>
      <span>Click me</span>
    </Button>
    <SendMailModal />

  </div>
</template>

<script setup lang="ts">
import SendMailModal from "@/components/SendMailModal.vue";
import Button from "@/components/ui/button/Button.vue";
console.log("dd");

</script>

<style scoped>
/* Puedes eliminar estos estilos ya que ahora están en Tailwind CSS */
</style>
