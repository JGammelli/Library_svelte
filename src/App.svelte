<script>
	import Library from "./Library.svelte";
</script>

<main>
	<h1>Library of Books</h1>
	<div><Library/></div>
</main>

<style>
	:global(body){
		background: black;
		position: relative;
		padding: 0;
		margin: 0;
	}
	h1{
		color: whitesmoke;
		text-align: center;
	}
	main{
		
	}
	div{
		position: absolute;
		width: 50vw;
		top: 20%; 
		left: 50%; 
		transform: translate(-50%, -50%);
	}

</style>