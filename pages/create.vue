<template>
  <form @submit.prevent="saveProducte" class="max-w-sm mx-auto">
    <div class="mb-5">
      <label
        for="large-input"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
        >PRODUCT NAME</label
      >
      <input
        v-model="producte.title"
        type="text"
        id="large-input"
        class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-base focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
      />
    </div>
    <div class="mb-5">
      <label
        for="message"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
        >DESCRIPTION</label
      >
      <textarea
        v-model="producte.description"
        id="message"
        rows="4"
        class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
        placeholder="Write a Good Descripton ..."
      ></textarea>
    </div>
    <div class="mb-5">
      <label
        for="base-input"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
        >CATEGORY</label
      >
      <input
        v-model="producte.category"
        type="text"
        id="base-input"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
      />
    </div>
    <div>
      <label
        for="small-input"
        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
        >PRICE</label
      >
      <input
        v-model="producte.price"
        type="text"
        id="small-input"
        class="block w-full p-2 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-xs focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
      />
    </div>

    <div class="mt-6 flex items-center justify-end gap-x-6">
      <NuxtLink
        to="/"
        class="relative inline-flex items-center justify-center p-0.5 mb-2 me-2 overflow-hidden text-sm font-medium text-gray-900 rounded-lg group bg-gradient-to-br from-purple-600 to-blue-500 group-hover:from-purple-600 group-hover:to-blue-500 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-blue-300 dark:focus:ring-blue-800"
      >
        <span
          class="relative px-5 py-2.5 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-md group-hover:bg-opacity-0"
        >
          Cancel
        </span>
      </NuxtLink>

      <button
        class="relative inline-flex items-center justify-center p-0.5 mb-2 me-2 overflow-hidden text-sm font-medium text-gray-900 rounded-lg group bg-gradient-to-br from-purple-600 to-blue-500 group-hover:from-purple-600 group-hover:to-blue-500 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-blue-300 dark:focus:ring-blue-800"
      >
        <span
          class="relative px-5 py-2.5 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-md group-hover:bg-opacity-0"
        >
          Save
        </span>
      </button>
    </div>
  </form>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      producte: {
        title: "",
        description: "",
        category: "",
        price: "",
      },
    };
  },
  methods: {
    async saveProducte() {
      axios
        .post(`http://localhost:3000/products`, this.producte)
        .then((response) => {
          // useState(response.data.data);
          console.log(response);
          
        });
        await navigateTo({ path: '/' })
    },
  },
};
</script>

<style></style>
