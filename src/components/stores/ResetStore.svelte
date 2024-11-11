<script>
  import { count } from "./store";
  function resetCount() {
    // call the store variable.set to set the data to a specific amount rather than update (in the Increment and Decrement components )
    count.set(0);
  }
</script>

<button on:click={resetCount}>Reset</button>
