<template>
    <div class="container mx-auto bg-gray-200 rounded-xl shadow border p-8 m-10">
      <h2 class="text-3xl text-gray-700 font-bold mb-5">Categories:</h2>
      <ul class="text-3xl text-gray-700 font-bold mb-5 list-disc">
        <li v-for="category in categories" :key="category.id" @click="showClues(category.id)" :class="{ selected: category.id === selectedCategoryId }">
            {{ category.title }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        categories: [],
        selectedCategoryId: null,
      };
    },
    mounted() {
      axios
        .get('http://jservice.io/api/categories?count=5')
        .then(response => {
          this.categories = response.data;
        })
        .catch(error => {
          console.log(error);
        });
    },
    methods: {
      showClues(categoryId) {
        // TODO: Show clues for selected category
        this.selectedCategoryId = categoryId;
        this.$emit('category-selected', categoryId);
      },
    },
  };
  </script>

<style scoped>
@tailwind base;
@tailwind components;
@tailwind utilities;
</style>