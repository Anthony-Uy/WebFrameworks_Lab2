<!-- <script>
    import axios from 'axios';
    import { onMount } from 'svelte';
  
    export let category;
  
    let clues = [];
  
    onMount(() => {
      axios.get(`http://jservice.io/api/clues?category=${category}`)
        .then(response => {
          clues = response.data;
        })
        .catch(error => {
          console.error(error);
        });
    });
  </script>
  
  <h2>Clues</h2>
  
  <ul>
    {#each clues as clue}
      <li>{clue.question}</li>
    {/each}
  </ul> -->

  <script>
    import { onMount } from 'svelte';
    import axios from 'axios';
  
    export let category;
  
    let clues = [];
  
    const handleCategoryClick = async () => {
      const response = await axios.get(`http://jservice.io/api/clues?category=${category.id}`);
      clues = response.data;
    };
  
    $: {
      if (category) {
        handleCategoryClick();
      }
    }
  </script>
  
  <h2>Clues</h2>
  
  {#if clues.length > 0}
    <ul>
      {#each clues as clue}
        <li>{clue.question}</li>
      {/each}
    </ul>
  {:else}
    <p>No clues to display</p>
  {/if}
  
  