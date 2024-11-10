<!-- Declare a context:module script tag -->
<script context="module">
  let totalCount = 0;
  export function getTotalCount() {
    return totalCount;
  }
</script>

<script>
  let counter = 0;
  function handleCount() {
    counter += 1;
    totalCount += 1;
  }
</script>

<h3>Counter: {counter}</h3>
<button on:click={handleCount}>Increment Counter</button>
