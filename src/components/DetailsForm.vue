<template>
  <header class=" flex justify-end px-10 py-4">
    <button class=" bg-indigo-500 hover:bg-indigo-600 text-white py-2 px-4 rounded-xl focus-within:outline-none" @click="handleSignOut">Logout</button>
  </header>
  <div class="min-h-screen flex items-center justify-center">
    <div class="bg-white p-8 shadow-2xl rounded-lg w-96">
      <h2 class="text-2xl font-semibold mb-6">Personal Information</h2>
      <form @submit.prevent="submitForm">
        <div class="mb-4">
          <label for="name" class="block text-gray-600">Name</label>
          <input
            v-model="formData.name"
            type="text"
            id="name"
            name="name"
            :class="{ 'border-red-500': formErrors.name }"
            class="mt-1 block w-full border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
          />
          <p v-if="formErrors.name" class="text-red-500 text-sm mt-1">Name is required.</p>
        </div>
        <div class="mb-4">
          <label for="fatherName" class="block text-gray-600">Father's Name</label>
          <input
            v-model="formData.fatherName"
            type="text"
            id="fatherName"
            name="fatherName"
            :class="{ 'border-red-500': formErrors.fatherName }"
            class="mt-1 block w-full border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
          />
          <p v-if="formErrors.fatherName" class="text-red-500 text-sm mt-1">
            Father's Name is required.
          </p>
        </div>
        <div class="mb-4">
          <label for="motherName" class="block text-gray-600">Mother's Name</label>
          <input
            v-model="formData.motherName"
            type="text"
            id="motherName"
            name="motherName"
            :class="{ 'border-red-500': formErrors.motherName }"
            class="mt-1 block w-full border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
          />
          <p v-if="formErrors.motherName" class="text-red-500 text-sm mt-1">
            Mother's Name is required.
          </p>
        </div>
        <div class="mb-4">
          <label for="age" class="block text-gray-600">Age</label>
          <input
            v-model.number="formData.age"
            type="number"
            id="age"
            name="age"
            :class="{ 'border-red-500': formErrors.age }"
            class="mt-1 block w-full border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
          />
          <p v-if="formErrors.age" class="text-red-500 text-sm mt-1">Age is required.</p>
        </div>
        <div class="mb-6">
          <label for="address" class="block text-gray-600">Address</label>
          <textarea
            v-model="formData.address"
            id="address"
            name="address"
            :class="{ 'border-red-500': formErrors.address }"
            rows="3"
            class="mt-1 block w-full border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
          ></textarea>
          <p v-if="formErrors.address" class="text-red-500 text-sm mt-1">Address is required.</p>
        </div>
        <div class="flex items-center justify-between">
          <button
            type="submit"
            class="bg-indigo-500 hover:bg-indigo-600 text-white font-semibold py-2 px-4 rounded focus:outline-none focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
          >
            Submit
          </button>
          <!-- Optionally, you can add a "Reset" button to clear the form -->
          <!-- <button type="reset" class="bg-red-500 hover:bg-red-600 text-white font-semibold py-2 px-4 rounded focus:outline-none focus:ring focus:ring-red-200 focus:ring-opacity-50">Reset</button> -->
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
 
  data() {
    return {
      formData: {
        name: '',
        fatherName: '',
        motherName: '',
        age: null,
        address: ''
      },
      formErrors: {}
    }
  },
  methods: {
    validateForm() {
      this.formErrors = {}

      if (!this.formData.name) {
        this.formErrors.name = true
      }

      if (!this.formData.fatherName) {
        this.formErrors.fatherName = true
      }

      if (!this.formData.motherName) {
        this.formErrors.motherName = true
      }

      if (!this.formData.age) {
        this.formErrors.age = true
      }

      if (!this.formData.address) {
        this.formErrors.address = true
      }

      // Return true if the form is valid (no errors), otherwise false
      return Object.keys(this.formErrors).length === 0
    },
    
    submitForm() {
      if (this.validateForm()) {
        // Form is valid, you can proceed with form submission or any other logic
        console.log(this.formData)
      } else {
        // Form is invalid, handle the error (e.g., show a message)
        console.error('Form is invalid. Please fill in all required fields.')
      }
    },
    handleSignOut() {
      this.$router.push("/login");
    
  }
    
  }
}

</script>
