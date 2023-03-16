<script>
  import CategoryList from "./lib/CategoryList.svelte";
  import ClueList from "./lib/ClueList.svelte";
  import "./app.css";

  let categoryID;
  
  function getID(id){
    console.log(id);
    categoryID = id;
  }

</script>

<main>
  <CategoryList getID={getID}></CategoryList>
  {#if categoryID}
  <ClueList id={categoryID}></ClueList>
  {/if}
</main>
