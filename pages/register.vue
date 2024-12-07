<template>
  <div class="register-page">
    <h1>Register</h1>
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="username">Username:</label>
        <Input type="text" id="username" placeholder="Username" v-model="username" />
      </div>
      <div>
        <label for="password">Password:</label>
        <Input type="password" id="password" placeholder="Password" v-model="password" />
      </div>
      <div>
        <label for="email">Email:</label>
        <Input type="email" id="email" placeholder="Email" v-model="email" />
      </div>
      <div>
        <!-- @click es para el router de vue)?-->
        <Button variant="link" @click=goLogin >Already have an account? Login</Button>
      </div>
      <Button type="submit">Register</Button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { Button } from "../components/ui/button"
import { Input } from "../components/ui/input"
import { useRouter } from 'vue-router';

const router = useRouter();

const username = ref("");
const password = ref("");
const email = ref("");

const handleSubmit = () => {
  // Handle form submission
  console.log("Username:", username.value);
  console.log("Password:", password.value);
  console.log("Email:", email.value);
};

const goLogin = () => {
  router.push('/login');
};
</script>

<style scoped>
.register-page {
  padding: 20px;
  background-color: #f0f0f0;
}

form {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 5px;
}

input {
  margin-bottom: 10px;
  padding: 5px;
}

button {
  padding: 10px;
  background-color: #333;
  color: white;
  border: none;
  cursor: pointer;
}

</style>
