<div>
  <div>
    <slot name="header"></slot>
  </div>
  <div>
    <slot name="content"></slot>
  </div>
  <!-- you can make an if block to check if there is data for this slot coming from the parent  -->
  <!-- the syntax is {#if $$slots.footer-slot} -->
  <!-- Then close the if after the slot  -->
  {#if $$slots.footer}
    <div>
      <slot name="footer"></slot>
    </div>
  {/if}
</div>
