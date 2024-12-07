<template>
  <div class="login-page">
    <h1>Login</h1>
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
        <Button variant="link" @click=goRegister >Don't have an account? Register</Button>
      </div>
      <Button type="submit">Login</Button>
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

const handleSubmit = () => {
  // Handle form submission
  console.log("Username:", username.value);
  console.log("Password:", password.value);
};

const goRegister = () => {
  router.push('/register');
};

</script>

<style scoped>
.login-page {
  padding: 100px;
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
  margin-bottom: 5px;
  padding: 5px;
}

button {
  padding: 20px;
  background-color: #0C0A09;
  color: white;
  border: none;
  cursor: pointer;
}
</style>
