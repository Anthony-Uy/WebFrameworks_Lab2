<script>
    
    import axios from "axios";
    import { onMount } from "svelte";

    let categories =[];
    export let getID;

    async function getCategories(){
        let data = await axios.get('http://jservice.io/api/categories?count=5').then(response => {return response.data});
        return data;
    }

    onMount(async()=>{
        categories = await getCategories();
    })
</script>

<main>
    
    <div class="container mx-auto bg-gray-200 rounded-xl shadow border p-8 m-10">
    <h1 class="text-3xl text-gray-700 font-bold mb-5"> Categories</h1>    
        <ul class="text-3xl text-gray-700 font-bold mb-5 list-disc">
            {#each categories as category}
                <li on:click={getID(category.id)}>{category.title}</li>
            {/each}
        </ul>
    </div>
</main>