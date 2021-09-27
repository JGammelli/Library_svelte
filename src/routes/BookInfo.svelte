<script>
    import { Link } from "svelte-routing";
    import UpdateData, {borrow} from "../functions/UpdateData.svelte";
    export let books = [];
    let book;
    

    let bookId = localStorage.getItem("currentBook");

    if(window.localStorage.getItem("bookInfo") === null){
        localStorage["bookInfo"] = JSON.stringify([]);
    }  

    
    for(let bookInfo in books){
        if(JSON.stringify(books[bookInfo].id) === bookId){
            
            localStorage.setItem("bookInfo", JSON.stringify(books[bookInfo]));
            book = JSON.parse(localStorage.getItem("bookInfo"));
        }
    }

    let isBorrowed; 
    let bookBorrowed = book.borrowed;
    $:if(bookBorrowed === false){
        isBorrowed = "available"
    }else{
        isBorrowed = "unavailable"
    }


</script>

<div>
    <Link to="/"><p>Back</p></Link>

    <h3 id={book.id} >{book.title}</h3> <p>{book.author}</p>
    <button on:click={borrow(bookBorrowed, book)}>{isBorrowed}</button>

    <!-- svelte-ignore a11y-img-redundant-alt -->
    <img id={book.id} src={book.image} alt="image of the book cover" height="300"/>
</div>

<style>

</style>