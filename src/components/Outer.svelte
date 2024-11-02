<script>
    import Inner from "./Inner.svelte";
</script>
<!-- with no assignment then the Outer component will 'emit' this event one level up -->
<Inner on:greet />