<script>
  export let value;
</script>

<div class="tip-amount-container">
  <div class="text-container">
    <p>Tip Amount</p>
    <small>/ person</small>
  </div>
  <p class="value">${value.toFixed(2)}</p>
</div>

<style>
  .tip-amount-container {
    display: flex;
    justify-content: space-between;
    font-size: 1rem;
    margin-bottom: 2rem;
  }
  p {
    margin: 0;
    font-weight: 700;
    color: #fff;
  }
  small {
    font-size: 0.875rem;
    color: hsl(184, 14%, 56%);
  }

  .value {
    font-weight: bold;
    font-size: 2.25rem;
    color: hsl(172, 67%, 45%);
  }
</style>
