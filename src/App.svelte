<script>
  import Input from "./Input.svelte";
  import CustomInput from "./CustomInput.svelte";
  import TipButton from "./TipButton.svelte";
  import TipAmount from "./TipAmount.svelte";
  let tipPercent = [5, 10, 15, 25, 50];

  let bill = 0;
  let people = 0;
  let tip = 0;
  let tipAmount = 0;
  let total = 0;

  const setTip = ({ detail }) => {
    tip = parseInt(detail.tip);
  };
  const setBill = ({ detail }) => {
    bill = parseInt(detail.bill);
  };
</script>

<main class="container">
  <img src="./logo.svg" alt="Splitter" class="mb-3" />
  <div class="bg-white main-card">
    <div class="card-a">
      <p class="label">Bill</p>
      <Input imageUrl={`../icon-dollar.svg`} />
      <p class="label">Select tip %</p>
      <div class="button-inputs">
        {#each tipPercent as tip_ (tip_)}
          <TipButton
            on:setTip={setTip}
            text={tip_}
            active={tip_ === tip ? true : false}
          />
        {/each}
        <CustomInput />
      </div>
      <p class="label">Number of People</p>
      <Input on:setBill={setBill} imageUrl={`../icon-person.svg`} />
    </div>
    <div class="card-b">
      <TipAmount value={tipAmount} />
      <TipAmount value={total} />
      <button class="reset-btn">Reset</button>
    </div>
  </div>
</main>

<style>
  .main-card {
    padding: 1rem;
    border-radius: 0.9rem;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 3rem;
    width: 60%;
    padding: 3rem;
  }
  .card-a {
    width: 100%;
  }
  .card-b {
    background-color: hsl(183, 100%, 15%);
    padding: 3rem;
    border-radius: 15px;
  }
  .label {
    font-size: 0.8rem;
    font-weight: bold;
    color: hsl(186, 14%, 43%);
  }

  .button-inputs {
    display: grid;
    grid-template: repeat(2, 1fr) / repeat(3, 1fr);
    gap: 0.8rem;
  }

  .reset-btn {
    font-size: 1.375rem;
    text-transform: uppercase;
    background: hsl(172, 67%, 45%);
    color: hsl(183, 100%, 15%);
    padding: 0.5rem;
    border: none;
    font-weight: 900;
    border-radius: 0.3rem;
    width: 100%;
    margin-top: 3.5rem;
    font-family: "Space Mono", monospace;
  }

  .reset-btn:disabled {
    opacity: 0.3;
    pointer-events: none;
  }
</style>
