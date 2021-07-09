<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let text;
  export let active;
</script>

<button
  class:active
  type="button"
  on:click={() => dispatch("setTip", { tip: text })}
>
  {text}%
</button>

<!-- <button></button> -->
<style>
  button {
    background-color: hsl(183, 100%, 15%);
    color: #fff;
    width: 100%;
    padding: 0.375em;
    border: none;
    border-radius: 5px;
    font-size: 1.5rem;
    font-weight: bold;
    cursor: pointer;
    font-family: "Space Mono", monospace;
  }
  button:hover {
    background: hsl(185, 41%, 84%);
    color: hsl(183, 100%, 15%);
  }
  .active {
    background: hsl(172, 67%, 45%) !important;
    color: hsl(183, 100%, 15%);
  }
</style>
