<script>
  let billAmount = $state(0); //bill amount is $0 by default, until user inputs a value
  let tipPercent = $state(20);
  let numPeople = $state(1);
  let tip = $derived(billAmount * (tipPercent / 100));
  let total = $derived(billAmount + tip);
  let perPerson = $derived(total / numPeople);
</script>

<div class="page-center">
  <div class="calculator">
  <h3>Tip Calculator</h3>

<div class="input-group">
    <label for="percent">Tip {tipPercent}%</label>
    <input
        type="range"
        id="percent"
        bind:value={tipPercent}
        min="10"
        max="30"
        step="1"
    >
  </div>

 <div class="input-group">
    <label for="people">Split between {numPeople} {numPeople === 1 ? 'person' : 'people'}</label>
    <input type="number" id="people" bind:value={numPeople} min="1">
  </div>

  <div class="input-group">
    <label for="bill">Bill Amount</label>
    <div class="input-wrapper">
      <span class="currency">$</span>
      <input 
        type="number"
        id="bill"
        bind:value={billAmount}
        min="0"
        step="0.01"
      >
    </div>
  </div>

  <div class="result"> <!-- custom tip percentage -->
    <span class="label">{tipPercent}% Tip</span>
    <span class="value">${tip.toFixed(2)}</span>
  </div>

  <div class="result">
  <span class="label">Total</span>
  <span class="value">${total.toFixed(2)}</span>
  </div>
</div>

{#if numPeople > 1}
  <div class="result">
      <span class="label">Per Person</span>
      <span class="value">${perPerson.toFixed(2)}</span>
  </div>
  {/if}

</div>

<style>
  .calculator {
    padding: 1.5rem;
    margin: 0 auto;
    background: var(--color-light-gray);
    margin: 2rem 0;
    max-width: 400px;
    text-align: center;
  }

  .page-center {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem;
    box-sizing: border-box;
    background: transparent;
  }

  h3 {
    margin: 0 0 1.5rem !important;
    font-weight: bold !important;
    font-size: 1.75rem !important;
    text-transform: uppercase;
  }

  .input-group {
    margin-bottom: 1.5rem;
  }

  label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: bold;
  }

  .input-wrapper {
    display: flex;
    align-items: center;
    border: 2px solid #ddd;
  }

  .currency {
    padding: 0.75rem;
    background: #eee;
    font-weight: bold;
  }

  input[type="number"] {
    flex: 1;
    padding: 0.75rem;
    border: none;
    font-size: 1.25rem;
    width: 100%;
  }

  .result {
    padding: 1rem;
    background: var(--color-accent);
    color: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .result .value {
    font-size: 1.5rem;
    font-weight: bold;
  }
</style>