
<script setup>
import { useRouter, useRoute } from 'vue-router'
import { ref } from 'vue'
import { useAuth } from '@/composables/useAuth'
const { login, logout } = useAuth()

const route = useRoute()
const router = useRouter()


const username = ref('')
const password = ref('')

 const logUserIn = async () => {
    if (await login(username.value, password.value)) {
      if (route.query.redirect) {
        router.push(route.query.redirect)
      } else {
        router.push({ name: 'Home' })
      }
    } else {
      logout()
    }
  }
</script>
<template>
    <form class="login-form" @submit.prevent="logUserIn">
        <input v-model="username" type="text" placeholder="Username" />
        <input v-model="password" type="password" placeholder="Password" />
    <button type="submit" class=" bg-green-500 px-4 py-2">Log In</button>
    </form>
</template>

<style scoped lang="postcss">
.login-form {
    @apply flex flex-col max-w-md mt-80 gap-4 mx-auto p-8 bg-white rounded-md shadow-lg; 

    & input {
        @apply text-xl px-4 ring-1 rounded-md ring-slate-300;
    }
}
</style>