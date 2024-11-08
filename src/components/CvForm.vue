<template>
  <div>
    <h2>CV Form</h2>
    

    <form class="max-w-sm mx-auto" @submit.prevent="submitForm">
      <div class="mb-5">
        <label for="Name" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Name</label>
        <input v-model="formData.name" type="text" id="Name" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light" placeholder="name@flowbite.com" required />
      </div>
      <div class="mb-5">
        <label for="Address" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Address</label>
        <input v-model="formData.address" type="text" id="Address" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light" placeholder="name@flowbite.com" required />
      </div>
      <div class="mb-5">
        <label for="Email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Email</label>
        <input v-model="formData.email" type="text" id="Email" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light" placeholder="name@flowbite.com" required />
      </div>
      <div class="mb-5">
        <label for="Expertise" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Expertise</label>
        <input v-model="formData.expertise" type="text" id="Expertise" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light" placeholder="name@flowbite.com" required />
      </div>
      <div class="mb-5">
        <label for="Education" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Education</label>
        <input v-model="formData.education" type="text" id="Education" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light" placeholder="name@flowbite.com" required />
      </div>
      <div class="mb-5">
        <label for="Skills" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Skills</label>
        <input v-model="formData.skills" type="text" id="Skills" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light" placeholder="name@flowbite.com" required />
      </div>

      <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Register new account</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        name: '',
        address: '',
        email: '',
        expertise: '',
        education: '',
        skills: ['JavaScript', 'Vue.js', 'Node.js', 'Laravel', 'HTML', 'CSS'],
      },
    };
  },
  methods: {
    submitForm() {
      // Emit the form data to the parent component
      this.$emit('form-submitted', this.formData);
    },
  },
};
</script>

<style scoped>
/* Add styles for the form here */
</style>
