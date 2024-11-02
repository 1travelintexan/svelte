<script>
    //import the dispatcher from svelte
    import {createEventDispatcher} from 'svelte'
    //create a variable that is the dipatcher invoked
    const dispatch = createEventDispatcher()
function handleGreet(){
    console.log('greet clicked inner')
    //to dispatch the event you call the variable and give it 2 arguments. The name and the data
    dispatch('greet', 'this is details from inner')
}
</script>
<button on:click={handleGreet}>Greet</button>