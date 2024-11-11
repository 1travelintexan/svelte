<script>
  import { count } from "./store";
  function decrement() {
    // call the count .update to adjust the value. You get a callback with the previous value as the argument
    count.update((prev) => {
      return (prev -= 1);
    });
  }
</script>

<button on:click={decrement}>Decrement</button>
