<template>
  <main class="flex flex-row justify-center items-center h-full w-full">
    <div class=" h-[600px] flex justify-center shadow-2xl w-1/2">
    <div class="w-1/2  h-screen flex justify-center items-center mb-10">

      <img src="../assets/AdobeStock_119115529_Preview.jpeg" class=" h-1/2  w-full rounded-xl"/>
    </div>
    <div class=" w-1/2 flex flex-col justify-center items-center">
      <h1 class="text-lg font-semibold">Login With Google</h1>
      <button class="mt-5 bg-pink-500 text-white px- py-2 rounded-xl w-28" @click="signInWithGoogle">
        Login
      </button>
    </div>
  </div>
  </main>
</template>

<script>
export default {
  methods: {
    signInWithGoogle() {
      this.$router.push('/')
    }
  }
  
}
</script>
