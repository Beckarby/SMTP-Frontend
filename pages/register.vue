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
          <Label for="email">Email</Label>
          <Input
            id="email"
            type="email"
            placeholder="elatla@uru.edu"
            required
            v-model="email"
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

const password = ref("");
const email = ref("");
const name = ref("");

const handleSubmit = async (event: Event) => {
  try {
    const response = await fetch('http://shadedcitadel.xyz:8443/auth/register', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        email: email.value,
        password: password.value,
        name: name.value
      })
    });

    if (response.ok) {
      router.push('/login');
    } else if (response.status === 409) {
      alert("A user with the provided email already exists");
    } else {
      console.error("An error occurred during registration:", response.statusText);
    }
  } catch (error) {
    console.error("An error occurred during registration:", error);
  }
};

const goLogin = () => {
  console.log("Email:", email.value);

console.log("Go to login");



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
