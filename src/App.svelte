<script>
  import svelteLogo from "./assets/svelte.svg";
  import { setContext } from "svelte";
  import Greet from "./components/Greet.svelte";
  import GreetWithProps from "./components/GreetWithProps.svelte";
  import Outer from "./components/Outer.svelte";
  import Button from "./components/Button.svelte";
  import CardSlot from "./components/CardSlot.svelte";
  import NamedSlot from "./components/NamedSlot.svelte";
  //create a variable to send as props
  let firstName = "Clark";
  let lastName = "Kent";
  const obj = {
    name: "Tony",
    lastName: "Stark",
  };
  //after importing, you call setContext with a name and value
  // go to Greet component to see how to receive it
  setContext("first-name", firstName);

  //this function runs with the nested component(Inner) is clicked
  //the details come from the Inner, and go to the Outer component.
  //in the Outer you need to put on:greet with no assignment to 'emit' the event to the parent (App.svelte)
  //you will receive the data in the event.detail property
  function handleGreetApp(event) {
    console.log("hello from app", event);
    alert(event.detail);
  }
</script>

<main>
  <h1>Standard Component:</h1>
  <!-- standard componenet call -->
  <Greet />
  <h1>Sending Props:</h1>
  <!-- pass props to component -->
  <GreetWithProps name="Bruce" lastName="Wayne" />
  <!-- sending props that are variables in parent component  -->
  <GreetWithProps name={firstName} {lastName} />
  <!-- sending props that are an obj and spreading it -->
  <GreetWithProps {...obj} />
  <h1>Event Forwarding:</h1>
  <!-- event forwarding -->
  <Outer on:greet={handleGreetApp} />
  <h1>Inline on:click called</h1>
  <Button on:click={() => alert("test")} />
  <!-- basic slots example  -->
  <!-- perfect for sending html rather than just string data -->
  <CardSlot>test without html</CardSlot>
  <CardSlot><h1>Card 1 H1</h1></CardSlot>
  with default content on the slot
  <CardSlot />
  <!-- named slot examples  -->
  <!-- this is for a component with multiple slots to specify what content goes to which slot  -->
  <!-- you need to provide the same number of divs for the slots in the component  -->
  <!-- Then on the outer most html... give a slot attribute that equals the name attribute on the slot in the component -->
  <!-- look in the NamedSlot component to see that there are 3 slots with names that correspond to the slot = here on the parent  -->
  <NamedSlot>
    <div slot="header"><h2>content for header slot</h2></div>
    <div slot="content"><h5>content for content slot</h5></div>
    <div slot="footer"><button>content for footer slot</button></div>
  </NamedSlot>
</main>

<style>
</style>
