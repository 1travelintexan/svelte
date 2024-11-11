<script>
  import { count } from "../stores/store";
  let counter;
  count.subscribe((prevValue) => {
    counter = prevValue;
  });
</script>

<h2>The Store Count is: {counter}</h2>
