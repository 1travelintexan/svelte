<script>
  import { count } from "../stores/store";
  function increment() {
    // call the count .update to adjust the value. You get a callback with the previous value as the argument

    count.update((prev) => {
      return (prev += 1);
    });
  }
</script>

<button on:click={increment}>Increment</button>
