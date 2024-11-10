<script>
  import { onMount } from "svelte";

  let posts = [];
  //onMount comes from svelte when page first loads
  // it expects a function as a parameter
  onMount(async () => {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    let data = await res.json();
    // reassign post variable
    //grab first 5 bc its too big
    posts = data.slice(0, 5);
    console.log("here are the posts", posts);
  });
</script>

{#each posts as post}
  <h4>Title: {post.title}</h4>
  <p>{post.body}</p>
{:else}
  <p>Loading...</p>
{/each}
