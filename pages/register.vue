<template>
  
  <div class="pt-11">
    <form @submit.prevent="handleSubmit">
      <Card class="mx-auto max-w-sm pt-4">
    <CardHeader>
      <CardTitle class="text-2xl text-[#22B357]">
        Register
      </CardTitle>
      <CardDescription>
        Enter your information below to make your account
      </CardDescription>
    </CardHeader>
    <CardContent>
      <div class="grid gap-2">
        <div class="grid gap-2">
          <Label for="username">Username</Label>
          <Input
            id="username"
            type="text"
            placeholder="elatla"
            required
            v-model="username"
          />
        </div>
        <div class="grid gap-2">
          <div class="flex items-center">
            <Label for="password">Password</Label>
          </div>
          <Input 
            id="password" 
            type="password" 
            placheholder="delunoalocho" 
            required 
            v-model="password" 
          />
        </div>
        <div class="grid gap-2">
          <div class="flex items-center">
            <Label for="email">Email</Label>
          </div>
          <Input 
            id="email" 
            type="email" 
            placheholder="elatla@uru.edu" 
            required 
            v-model="email" 
          />
        </div>
        <Button type="submit" class="w-full">
          Login
        </Button>
      </div>
      <div class="mt-4 text-center text-sm">
        Already have an account?
        <a @click=goLogin class="underline text-[#22B357]">
          Login
        </a>
      </div>
    </CardContent>
  </Card>
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
