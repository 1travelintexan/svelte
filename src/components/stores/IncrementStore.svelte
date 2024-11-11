<script>
  import { count } from "../stores/store";
  function increment() {
    count.update((prev) => {
      return (prev += 1);
    });
  }
</script>

<button on:click={increment}>Increment</button>
