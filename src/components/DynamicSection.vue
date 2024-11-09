<template>
    <div class="mb-5">
      <h3 class="font-bold mb-2 text-white">{{ title }}</h3>
      <div v-for="(item, index) in items" :key="index" class="space-y-2 mb-2">
        <div class="flex space-x-2 mb-2">
            <input v-model="item.date" type="text" class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Date" />
            <input
              v-model="item[fieldName]"
              type="text"
              class="input bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
              :placeholder="title === 'Work Experience' ? 'Position' : 'Degree'"
            />
        </div>
        <label for="message" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">description</label>
        <textarea v-model="item.description" rows="3" class="input block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Description"></textarea>
        <button @click="removeItem(index)" class="noselect"><span class="text">Remove</span><span class="icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M24 20.188l-8.315-8.209 8.2-8.282-3.697-3.697-8.212 8.318-8.31-8.203-3.666 3.666 8.321 8.24-8.206 8.313 3.666 3.666 8.237-8.318 8.285 8.203z"></path></svg></span></button>
      </div>

      <button @click.prevent="addItem" type="button" class="buttonAdd"><span class="button__text">Add</span><span class="button__icon"><svg xmlns="http://www.w3.org/2000/svg" width="24" viewBox="0 0 24 24" stroke-width="2" stroke-linejoin="round" stroke-linecap="round" stroke="currentColor" height="24" fill="none" class="svg"><line y2="19" y1="5" x2="12" x1="12"></line><line y2="12" y1="12" x2="19" x1="5"></line></svg></span></button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: String,
      items: Array,
      fieldName: String // Add fieldName prop to specify whether it's 'position' or 'degree'
    },
    methods: {
      addItem() {
        this.$emit('add-item');
      },
      removeItem(index) {
        this.$emit('remove-item', index);
      }
    }
  };
  </script>
  <style scoped>
  .input {
    width: 100%;
    padding: 0.5rem;
    border-radius: 0.25rem;
    border: 1px solid #ddd;
  }
  .btn {
    background-color: #007bff;
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 0.25rem;
    cursor: pointer;
  }
  .btn-primary {
    background-color: #0056b3;
  }
  .btn-danger {
    background-color: #dc3545;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 0.25rem;
  }
  </style>