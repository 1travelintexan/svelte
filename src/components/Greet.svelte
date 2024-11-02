<script>
// inside the script tag, import getContext from svelte  
import {
    getContext
} from "svelte";
//after you import, call get context with the name you gave it in App.svelte
const firstName = getContext('first-name')
</script>

<h3>Hello from Greet {firstName}</h3>
