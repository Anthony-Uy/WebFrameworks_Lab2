<script>
    import axios from "axios";
    import { onMount } from "svelte";

    export let id;
    let clues = [];

    async function getClues(id){
        let data = await axios.get(`http://jservice.io/api/clues?category=${id}`).then(response => {return response.data});
        return data;
        
    }

    onMount(async()=>{
        clues = await getClues(id);
    })
</script>

<main>
    
    <div class="container mx-auto bg-gray-200 rounded-xl shadow border p-8 m-10">
    <h1 class="text-3xl text-gray-700 font-bold mb-5"> Clues</h1>
        <ul class="text-3xl text-gray-700 font-bold mb-5 list-disc">
            {#each clues as clue}
                <li>{clue.question}</li>
            {/each}
        </ul>
    </div>
</main>