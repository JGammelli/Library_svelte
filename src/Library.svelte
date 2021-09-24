<script>
    import {onMount} from "svelte";
    import Book from "./Book.svelte";

    export let books = [];

    onMount(()=>{
        fetch("http://localhost:3000/books")
        .then(res => res.json())
        .then(data =>{
            books = data;
        })
    })

</script>



<div class="bookshelf">
    {#each books as book}
        <Book {book}/>
    {:else}
        <div>Bringing the books out</div>
    {/each}
</div>





<style>
    .bookshelf{
        display: flex;
        flex-wrap: wrap;
        position: absolute;
        height: fit-content;
    }
</style>