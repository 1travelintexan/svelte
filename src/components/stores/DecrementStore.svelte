<script>
  import { count } from "./store";
  function decrement() {
    count.update((prev) => {
      return (prev -= 1);
    });
  }
</script>

<button on:click={decrement}>Decrement</button>
