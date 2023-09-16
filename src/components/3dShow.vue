<template>
  <script src="./main.js" type="module">
  </script>
</template>

<script setup lang="ts">
import { useAuthStore } from '../stores/auth';
import { computed } from 'vue';
import { useRouter } from 'vue-router';

const authStore = useAuthStore()

const router = useRouter()

const user = computed(()=>{
  return authStore.user
})

const isAuthenticated = computed(()=>{
  return authStore.isAuthenticated
})

async function logout(){
  await authStore.logout()
    .then( res => {
      router.replace({name: 'home'})
    })
    .catch(err => {
      console.log(err.message)
    })
}

</script>