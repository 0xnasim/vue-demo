<template>
  <main class="flex h-screen">
    <div class="w-1/2 bg-pink-500"></div>
    <div class="w-1/2">
      <LoginComp />
    </div>
  </main>
</template>

<script setup>
import LoginComp from '../components/LoginComp.vue'
import { ref, watchEffect } from 'vue'
import { getAuth, onAuthStateChanged, signOut } from 'firebase/auth'
import { useRouter } from 'vue-router'

const router = useRouter()

const isLoggedIn = ref(true)

watchEffect(() => {
  if (!isLoggedIn.value) {
    router.push()
  }
}, [isLoggedIn])

onAuthStateChanged(getAuth(), function (user) {
  if (user) {
    isLoggedIn.value = true
  } else {
    isLoggedIn.value = false
  }
})

const handleSignOut = () => {
  signOut(getAuth())
  router.push('/')
}
</script>
