<template>
  <Button @click="goToEmail" class="w-full bg-white h-14 boton">
    <div
      class="flex  space-x-2 p-2 "
    >
      <div>{{ email }}</div>
      <div >📧</div>
    </div>
    <div>{{ subject }}</div>
  </Button>
</template>

<script setup lang="ts">
import { useRouter } from "vue-router";
import Button from "@/components/ui/button/Button.vue";

defineProps({
  email: String,
  subject: String,
});

const router = useRouter();

const goToEmail = () => {
  router.push("/mail");
};
</script>

<style scoped>
.boton {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-content: center;
}
.si {
  flex-direction: row;
}
</style>
