<template>
    <div class="container mx-auto bg-gray-200 rounded-xl shadow border p-8 m-10">
      <h2 class="text-3xl text-gray-700 font-bold mb-5">Clues:</h2>
      <ul class="text-3xl text-gray-700 font-bold mb-5 list-disc">
        <li v-for="clue in clues" :key="clue.id">
          {{ clue.question }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    props: {
      categoryId: {
        type: Number,
        required: true,
      },
    },
    data() {
      return {
        clues: [],
      };
    },
    mounted() {
      axios
        .get(`http://jservice.io/api/clues?category=${this.categoryId}`)
        .then(response => {
          this.clues = response.data;
        })
        .catch(error => {
          console.log(error);
        });
    },
  };
  </script>

<style scoped>
@tailwind base;
@tailwind components;
@tailwind utilities;
</style>