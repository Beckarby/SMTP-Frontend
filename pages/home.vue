<template>

  <div class="logout-button-wrapper">
    <Button @click="logout" class="logout-button">
      <span>Logout</span>
    </Button>
  </div>
  
    <h2 class="title text-white-900 text-4xl font-bold centered-title">SMTP CLIENT</h2>
    <div class="container">



      <div class="option-box">
        <div class="option">
          <div class="send-mail-modal-wrapper card">
            <SendMailModal />
          </div>
          <Button @click="useMockData1">
            <span>neerfen a moviles</span>
          </Button>
          <div class="separator"></div>
          <Button @click="useMockData2">
            <span>Incidente 2/12</span>
          </Button>
        </div>
      </div>
      <div class="email-list-box">
        <h3 class="email-list-title text-gray-800 text-xl font-bold">Emails Recibidos</h3>
        <div class="email-list bg-gray-300 rounded">
          <div class="email-item card p-1" v-for="email in emails" :key="email.id">
            <MailButton :email="email.email" :subject="email.subject" />
          </div>
        </div>
      </div>
    </div>

</template>

<script setup lang="ts">

import SendMailModal from "@/components/SendMailModal.vue";
import Button from "@/components/ui/button/Button.vue";
import MailButton from "@/components/MailButton.vue";
import { ref } from 'vue';

import { useRouter } from 'vue-router';
const router = useRouter();

const mockData1 = [
  { id: 1, email: 'example1@example.com', subject: 'Subject 1' },
];

const mockData2 = [
  { id: 20, email: 'example20@example.com', subject: 'Subject 20' }
];

const emails = ref(mockData1);

function useMockData1() {
  emails.value = mockData1;
}

function useMockData2() {
  emails.value = mockData2;
}

function logout() {
  // Implement your logout logic here
  console.log('User logged out');
  router.push('/login');
}

</script>

<style scoped>
.email-list {
  flex-direction: column;
  width: 100%;
}
.container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 100vw;
  height: 100vh;

}
.option {
  display: flex;
  flex-direction: column;
}

.option-box {
  width: 20%;
  padding: 10px;
  background-color: white;
  border-radius: 20px;
}

.email-list-box {  
  width: 79%;
  padding: 10px;
  background-color: white;
  border-radius: 20px;
}

.email-list-title {
  margin-bottom: 10px;
}

.separator {
  height: 10px;
}

.send-mail-modal-wrapper {
  margin-bottom: 20px;
  width: 100px;
}

.email-item {
  border-radius: 10px;
}

.centered-title {
  text-align: center;
  margin: 20px 0;
}

.logout-button-wrapper {
  position: absolute;
  top: 10px;
  right: 10px;
}

.logout-button {
  background-color: red;
  color: white;
}

</style>