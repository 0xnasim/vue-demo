<template>
  <main class="flex flex-col justify-center items-center h-full">
    <div>
      <h1 class="text-lg font-semibold">Login With Google</h1>
      <button class="mt-5 bg-pink-500 px-3 py-2 rounded-xl w-full" @click="signInWithGoogle">
        Login
      </button>
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
