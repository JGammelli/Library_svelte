<script context="module">

    export function borrow(bookBorrowed){

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