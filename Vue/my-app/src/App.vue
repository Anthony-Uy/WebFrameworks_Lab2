<template>
  <div>
    <CategoryList @category-selected="showClues" />
    <ClueList v-if="selectedCategoryId !== null" :category-id="selectedCategoryId" />
  </div>
</template>

<script>
import CategoryList from './components/CategoryList.vue';
import ClueList from './components/ClueList.vue';

export default {
  components: {
    CategoryList,
    ClueList,
  },
  data() {
    return {
      selectedCategoryId: null,
    };
  },
  methods: {
    showClues(categoryId) {
      this.selectedCategoryId = categoryId;
    },
  },
};
</script>

<style scoped>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>