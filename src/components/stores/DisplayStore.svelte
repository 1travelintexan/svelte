<script>
  import { onDestroy } from "svelte";
  import { count } from "../stores/store";

  let counter;
  const idToUnsubscribe = count.subscribe((prevValue) => {
    counter = prevValue;
  });
  onDestroy(idToUnsubscribe);
</script>

<h2>The Store Count is: {counter}</h2>
