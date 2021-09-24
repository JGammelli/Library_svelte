<script>
    export let book = {};
    
    
    let isBorrowed; 
    let bookBorrowed = book.borrowed;
    $:if(bookBorrowed === false){
        isBorrowed = "available"
    }else{
        isBorrowed = "unavailable"
    }


    const Borrow = () => {

        let setBorrowed = {"borrowed": !book.borrowed}

        fetch(`http://localhost:3000/books/${book.id}`, {
            method:"PATCH",
            headers: {
                "Content-type": "application/json"
            },
            
            body: JSON.stringify(setBorrowed)
        })
        .then(res => res.json())
        .then(data => console.log("Success", data))
        .catch(err => log("error", err))
        bookBorrowed = !bookBorrowed;
    }
</script>

<div>
    <h3>{book.title}</h3> <p>{book.author}</p>
    <button on:click={Borrow}>{isBorrowed}</button>

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
    button:hover{
        cursor: pointer;
    }
    img{
        grid-row-start: 3;
        padding-bottom: 1em;
        padding-top: 1em;
    }

</style>