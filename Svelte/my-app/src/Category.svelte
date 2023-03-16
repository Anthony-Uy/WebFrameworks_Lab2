
<!-- <script>
    import axios from 'axios';
    import { onMount } from 'svelte';
  
    export let onCategorySelected;
  
    let categories = [];
  
    onMount(() => {
      axios.get('http://jservice.io/api/categories?count=5')
        .then(response => {
          categories = response.data;
        })
        .catch(error => {
          console.error(error);
        });
    });
  
    function selectCategory(category) {
      onCategorySelected(category.id);
    }
  </script>
  
  <h2>Categories</h2>
  
  <ul>
    {#each categories as category}
      <li on:click={() => selectCategory(category)}>{category.title}</li>
    {/each}
  </ul> -->
  <script>
    import { onMount } from 'svelte';
    import axios from 'axios';
  
    let categories = [];
  
    onMount(async () => {
      const response = await axios.get('http://jservice.io/api/categories?count=5');
      categories = response.data;
    });
  </script>
  
  <h2>Categories</h2>
  
  <ul>
    {#each categories as category}
      <li>{category.title}</li>
    {/each}
  </ul>
  
  