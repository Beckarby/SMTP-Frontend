<template>
  <div class="login-page">
    <h1>Login</h1>
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" />
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" />
      </div>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const username = ref("");
const password = ref("");

const handleSubmit = () => {
  // Handle form submission
  console.log("Username:", username.value);
  console.log("Password:", password.value);
};
</script>

<style scoped>
.login-page {
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
