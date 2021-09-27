<script>
    import { Link } from "svelte-routing";
    import UpdateData, {borrow} from "./functions/UpdateData.svelte";
    export let book = {};
    
    
    let isBorrowed; 
    let bookBorrowed = book.borrowed;
    $:if(bookBorrowed === false){
        isBorrowed = "available"
    }else{
        isBorrowed = "unavailable"
    }

    let currentBook = (event) =>{
        localStorage.setItem("currentBook", event.target.id)
    }
    

</script>

<div>
    <Link to="bookInfo"><h3 on:click={currentBook} id={book.id} >{book.title}</h3></Link> <p>{book.author}</p>
    <button on:click={borrow(bookBorrowed, book)}>{isBorrowed}</button>

    <!-- svelte-ignore a11y-img-redundant-alt -->
    <Link to="bookInfo"><img on:click={currentBook} id={book.id} src={book.image} alt="image of the book cover" height="300"/></Link>
</div>


<style>
    div{
        height: fit-content;
        display: grid;
        grid-template-rows: 2em 2em 300px auto auto;
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
    button:hover{
        cursor: pointer;
    }
    img{
        grid-row-start: 3;
        padding-bottom: 1em;
        padding-top: 1em;
    }


</style>