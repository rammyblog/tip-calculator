<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let value;
</script>

<input
  bind:value
  placeholder="Custom"
  on:keyup={() => dispatch("setTip", { tip: value })}
/>

<style>
  input {
    width: 100%;
    border: none;
    padding: 0.2rem;
    border-radius: 0.1rem;
    background: hsl(189, 41%, 97%);
    color: hsl(184, 14%, 56%);
    font-size: 24px;
    font-family: "Space Mono", monospace;
  }
</style>
