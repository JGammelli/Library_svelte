<script>
    import { Router, Route } from 'svelte-routing';
    import BookInfo from "./BookInfo.svelte";
    import Library from "../Library.svelte";
    import {onMount} from "svelte";

    export let url = '';

    export let books = []
	onMount(()=>{
        fetch("http://localhost:3000/books")
        .then(res => res.json())
        .then(data =>{
            books = data;
        })
    })
</script>

<Router {url}>
    <Route {books} path="bookInfo" component={BookInfo } />
    <Route {books} path="/" component={Library} />
</Router>