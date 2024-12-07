<template>
  <div class="homepage bg-gray-100 justify-center items-center">
    <h2 class="title text-gray-800 text-2xl font-bold">Welcome to the homepage</h2>
    <SendMailModal />

    
    <div class="container" >
      <div class="option">
        <Button>
          <span>Click me</span>
        </Button>
        <Button>
          <span>Click me 2</span>
        </Button>
      </div>
    <div class="email-list">
      <div class="bg-gray-300 p-1 " v-for="i in 10" :key="i">
          <MailButton email="hola" subject="rebecca" />
      </div>
    </div>
        
        
        
        
        
    </div>
      


  </div>
</template>

<script setup lang="ts">

import SendMailModal from "@/components/SendMailModal.vue";
import Button from "@/components/ui/button/Button.vue";
import MailButton from "@/components/MailButton.vue";

</script>

<style scoped>
.email-list {
  flex-direction: column;
  width: 50%;
}
.container {
  display: flex;
  flex-direction: row;

}
.option {
  display: flex;
  flex-direction: column;
}

</style>