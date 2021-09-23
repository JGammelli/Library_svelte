<script>
    export let book = {};
    
    
    let isBorrowed; 
    if(book.borrowed === false){
        isBorrowed = "available"
    }else{
        isBorrowed = "unavailable"
    }
    console.log(book.image);
</script>

<div>
    <h3>{book.title}</h3> <p>{book.author}</p>
    <button>{isBorrowed}</button>

    <!-- svelte-ignore a11y-img-redundant-alt -->
    <img src={book.image} alt="image of the book cover" width="200"/>
</div>


<style>
    div{
        height: fit-content;
        display: grid;
        grid-template-rows: 2em 2em auto auto auto;
        grid-template-columns: 15em;
    }
    p{
        grid-row-start: 4;
    }
    h3{
        color: whitesmoke;
        grid-row-start: 1;
        grid-row-end: 2;
    }
    button{
        width:fit-content;
        grid-row-start: 5;
    }
    img{
        grid-row-start: 3;
        padding-bottom: 1em;
        padding-top: 1em;
    }

</style>