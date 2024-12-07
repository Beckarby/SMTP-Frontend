<template>
  <div class="homepage bg-gray-100 p-5 min-h-screen flex flex-col justify-center items-center">
    <h2 class="title text-gray-800 text-2xl font-bold">Welcome to the homepage</h2>
    <Button @click="goToPage">
      <span>Click me</span>
    </Button>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router';
import Button from '@/components/ui/button/Button.vue';

const router = useRouter();

const goToPage = () => {
  router.push('/login'); // Cambia '/another-page' por la ruta a la que quieres redirigir
};
</script>

<style scoped>
/* Puedes eliminar estos estilos ya que ahora están en Tailwind CSS */
</style>