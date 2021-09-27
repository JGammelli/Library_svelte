<script>

    import Book from "./Book.svelte";

    export let books = [];

    

</script>


<h1>Library of Books</h1>

<div class="libraryWrap">
    <div class="bookshelf">
        {#each books as book}
            <Book {book}/>
        {:else}
            <div>Bringing the books out</div>
        {/each}
    </div>
</div>




<style>
    .bookshelf{
        display: flex;
        flex-wrap: wrap;
        position: absolute;
        height: fit-content;
    }
    .libraryWrap{
		position: absolute;
		width: 50vw;
		top: 20%; 
		left: 50%; 
		transform: translate(-50%, -50%);
	}
    h1{
		color: whitesmoke;
		text-align: center;
	}
</style>