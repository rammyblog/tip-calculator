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
  let totalTip = 0;

  const setTip = ({ detail }) => {
    if (!detail.tip) {
      tip = 0;
    } else {
      tip = parseInt(detail.tip);
    }
    calculateTip();
  };
  const setBill = ({ detail }) => {
    if (!detail.value) {
      bill = 0;
    } else {
      bill = parseInt(detail.value);
    }
    calculateTip();
  };
  const setPeople = ({ detail }) => {
    if (!detail.value) {
      people = 0;
    } else {
      people = parseInt(detail.value);
    }
    calculateTip();
  };

  const calculateTip = () => {
    totalTip = bill + (bill * tip) / 100;
    tipAmount = (bill * tip) / 100;

    if (people) {
      tipAmount = (bill * tip) / 100 / people;
      totalTip = totalTip / people;
    }
  };

  const reset = () => {
    bill = 0;
    people = 0;
    tip = 0;
    tipAmount = 0;
    totalTip = 0;
  };
</script>

<main class="container">
  <img src="./logo.svg" alt="Splitter" class="mb-3 mt-2 image-center" />
  <div class="bg-white main-card">
    <div class="card-a">
      <p class="label">Bill</p>
      <Input on:setInputValue={setBill} imageUrl={`../icon-dollar.svg`} />
      <p class="label">Select tip %</p>
      <div class="button-inputs">
        {#each tipPercent as tip_ (tip_)}
          <TipButton
            on:setTip={setTip}
            text={tip_}
            active={tip_ === tip ? true : false}
          />
        {/each}
        <CustomInput on:setTip={setTip} />
      </div>
      <p class="label">Number of People</p>
      <Input on:setInputValue={setPeople} imageUrl={`../icon-person.svg`} />
    </div>
    <div class="card-b">
      <TipAmount text="Tip Amount" value={tipAmount} />
      <TipAmount text="Total" value={totalTip} />
      <button
        disabled={!bill && !people && !tip && !tipAmount && !totalTip}
        on:click={() => reset()}
        class="reset-btn">Reset</button
      >
    </div>
  </div>
  <div class="attribution">
    Challenge by <a
      href="https://www.frontendmentor.io?ref=challenge"
      target="_blank">Frontend Mentor</a
    >. Coded by
    <a href="https://github.com/rammyblog/tip-calculator">Babatunde Onasanya</a
    >.
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
    font-size: 12px;
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
  .attribution {
    font-size: 11px;
    text-align: center;
  }
  .attribution a {
    color: hsl(228, 45%, 44%);
  }
  @media (max-width: 600px) {
    .main-card {
      padding: 1rem;
      display: block;
      width: auto;
      padding: 1rem;
    }
    .container {
      display: block;
    }

    .reset-btn {
      margin-top: 1rem;
    }
    .image-center {
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 1rem auto;
    }
  }

  @media (max-width: 400px) {
    .button-inputs {
      grid-template-columns: 1fr 1fr;
    }
  }
</style>
