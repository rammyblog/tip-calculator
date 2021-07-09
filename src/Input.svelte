<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let value;
  export let imageUrl;

  let url = `url(${imageUrl}) no-repeat`;
</script>

<div class="input-icons" style="--url:{url}">
  <input
    bind:value
    class="input-field"
    type="text"
    placeholder="0"
    on:keyup={() => dispatch("setInputValue", { value })}
  />
</div>

<style>
  .input-icons {
    margin-bottom: 10px;
  }

  .input-field {
    width: 96%;
    text-align: right;
    border: 2px solid transparent;
    padding: 0.6rem;
    border-radius: 0.1rem;
    background: hsl(189, 41%, 97%);
    color: hsl(184, 14%, 56%);
    font-size: 24px;
    font-family: "Space Mono", monospace;
    outline: none;
    background: var(--url);
    background-position-x: 0%;
    background-position-y: 0%;
    background-position: 0.5em center;
  }
  .input-field:hover,
  .input-field:focus {
    border-color: hsl(172, 67%, 45%);
  }
</style>
