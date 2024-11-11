<script>
  import { onDestroy } from "svelte";
  import { count } from "../stores/store";

  let counter;
  // store the subscribe in a variable to be destroyed when the component is unmounted. ($count will also do the same )
  const idToUnsubscribe = count.subscribe((prevValue) => {
    counter = prevValue;
  });
  // this is for when the component is unmounted so no memory leaks
  onDestroy(idToUnsubscribe);
</script>

<h2>The Store Count is: {counter}</h2>
