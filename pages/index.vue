<template>


  
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

const mockData1 = [
  { id: 1, email: 'example1@example.com', subject: 'Subject 1' },
  { id: 2, email: 'example2@example.com', subject: 'Subject 2' },
  { id: 3, email: 'example3@example.com', subject: 'Subject 3' },
  { id: 4, email: 'example4@example.com', subject: 'Subject 4' },
  { id: 5, email: 'example5@example.com', subject: 'Subject 5' },
  { id: 6, email: 'example6@example.com', subject: 'Subject 6' },
  { id: 7, email: 'example7@example.com', subject: 'Subject 7' },
  { id: 8, email: 'example8@example.com', subject: 'Subject 8' },
  { id: 9, email: 'example9@example.com', subject: 'Subject 9' },
  { id: 10, email: 'example10@example.com', subject: 'Subject 10' }
];

const mockData2 = [
  { id: 11, email: 'example11@example.com', subject: 'Subject 11' },
  { id: 12, email: 'example12@example.com', subject: 'Subject 12' },
  { id: 13, email: 'example13@example.com', subject: 'Subject 13' },
  { id: 14, email: 'example14@example.com', subject: 'Subject 14' },
  { id: 15, email: 'example15@example.com', subject: 'Subject 15' },
  { id: 16, email: 'example16@example.com', subject: 'Subject 16' },
  { id: 17, email: 'example17@example.com', subject: 'Subject 17' },
  { id: 18, email: 'example18@example.com', subject: 'Subject 18' },
  { id: 19, email: 'example19@example.com', subject: 'Subject 19' },
  { id: 20, email: 'example20@example.com', subject: 'Subject 20' }
];

const emails = ref(mockData1);

function useMockData1() {
  emails.value = mockData1;
}

function useMockData2() {
  emails.value = mockData2;
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

</style>