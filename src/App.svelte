<script>
  import svelteLogo from "./assets/svelte.svg";
  import { setContext } from "svelte";
  import Greet from "./components/Greet.svelte";
  import GreetWithProps from "./components/GreetWithProps.svelte";
  import Outer from "./components/Outer.svelte";
  import Button from "./components/Button.svelte";
  import CardSlot from "./components/CardSlot.svelte";
  import NamedSlot from "./components/NamedSlot.svelte";
  import FetchComponent from "./components/FetchComponent.svelte";
  import AutoFocus from "./components/AutoFocus.svelte";
  import TabA from "./components/TabA.svelte";
  import TabB from "./components/TabB.svelte";
  import TabC from "./components/TabC.svelte";
  import Counter, { getTotalCount } from "./components/Counter.svelte";
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

  //this is for the dynamic components
  let activeTab = TabA;
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
  <!-- this is a test  fadf -->
  <NamedSlot>
    <div slot="header"><h2>content for header slot</h2></div>
    <div slot="content"><h5>content for content slot</h5></div>
    <div slot="footer"><button>content for footer slot</button></div>
  </NamedSlot>
  <!-- fetching data and looping over it component  -->
  <h2>Fetching Example:</h2>
  <FetchComponent />
  <!-- binding auto focus example  -->
  <AutoFocus />
  <hr />
  <!-- Dynamic components  -->
  <!-- three different components that render inside a div  -->
  <!-- In script on App there is a variable called active tab set to 'tabA' -->
  <!-- <button on:click={() => (activeTab = "TabA")}>Tab A</button>
  <button on:click={() => (activeTab = "TabB")}>Tab B</button>
  <button on:click={() => (activeTab = "TabC")}>Tab C</button>
  {#if activeTab === "TabA"}
    <TabA />
  {:else if activeTab === "TabB"}
    <TabB />
  {:else}
    <TabC />
  {/if} -->
  <!-- the same UI can be accomplished with the special svelte:component with the this={ a specific component you want to show}  -->
  <button on:click={() => (activeTab = TabA)}>Tab A</button>
  <button on:click={() => (activeTab = TabB)}>Tab B</button>
  <button on:click={() => (activeTab = TabC)}>Tab C</button>
  <svelte:component this={activeTab} />
  <!-- ***************special elements*************
  :component - for dynamic components
  :self - allows component to contain itself recursively
  :window -  Add event listeners to the window object
  :body - listen to events that fire on the document body
  :head - Insert elements inside the head of your document
  :options - specify complier options -->
  <h2>Module Context</h2>
  <h3>Here is the total count(module):</h3>
  <button on:click={() => alert(getTotalCount())}>total count</button>

  <Counter />
  <Counter />
  <Counter />
</main>

<style>
</style>
