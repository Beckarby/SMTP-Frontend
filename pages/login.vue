<template>
  
  <div class="pt-10">
    <form @submit.prevent="handleSubmit">
      <Card class="mx-auto max-w-sm pt-6">
    <CardHeader>
      <CardTitle class="text-2xl text-[#22B357]">
        Login
      </CardTitle>
      <CardDescription>
        Enter your information below to login to your account
      </CardDescription>
    </CardHeader>
    <CardContent>
      <div class="grid gap-4">
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
        <Button type="submit" class="w-full">
          Login
        </Button>
      </div>
      <div class="mt-4 text-center text-sm">
        Don't have an account?
        <a @click=goRegister class="underline text-[#22B357]">
          Register
        </a>
      </div>
    </CardContent>
  </Card>
    </form>
  </div>
  
</template>

<script setup lang="ts">
import { ref } from "vue";
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { useRouter } from 'vue-router'

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
