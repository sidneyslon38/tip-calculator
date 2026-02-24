<script>
   const prices = {
    netflix: 17.99,
    disney: 18.99,
    max: 18.49,
    hulu: 18.99,
    apple: 9.99,
    peacock: 10.99
  };

  let netflix = $state(false);
  let disney = $state(false);
  let max = $state(false);
  let hulu = $state(false);
  let apple = $state(false);
  let peacock = $state(false);

  let total = $derived(
  (netflix ? prices.netflix : 0) +
  (disney ? prices.disney : 0) +
  (max ? prices.max : 0) +
  (hulu ? prices.hulu : 0) +
  (apple ? prices.apple : 0) +
  (peacock ? prices.peacock : 0)
);
</script>

<div class="calculator">
  <button class="service" onclick={() => netflix = !netflix}>
    <span class="indicator">{netflix ? '✓' : '○'}</span>
    <span class="name">Netflix</span>
    <span class="price">${prices.netflix}/mo</span>
  </button>

  <button class="service" onclick={() => disney = !disney}>
    <span class="indicator">{disney ? '✓' : '○'}</span>
    <span class="name">Disney+</span>
    <span class="price">${prices.disney}/mo</span>
  </button>

  <button class="service" onclick={() => max = !max}>
    <span class="indicator">{max ? '✓' : '○'}</span>
    <span class="name">Max</span>
    <span class="price">${prices.max}/mo</span>
  </button>

  <button class="service" onclick={() => hulu = !hulu}>
    <span class="indicator">{hulu ? '✓' : '○'}</span>
    <span class="name">Hulu</span>
    <span class="price">${prices.hulu}/mo</span>
  </button>

  <button class="service" onclick={() => apple = !apple}>
    <span class="indicator">{apple ? '✓' : '○'}</span>
    <span class="name">Apple TV+</span>
    <span class="price">${prices.apple}/mo</span>
  </button>

  <button class="service" onclick={() => peacock = !peacock}>
    <span class="indicator">{peacock ? '✓' : '○'}</span>
    <span class="name">Peacock</span>
    <span class="price">${prices.peacock}/mo</span>
  </button>

  <div class="summary">
    <span class="summary-label">Monthly Total</span>
    <span class="summary-amount">${total.toFixed(2)}</span>
  </div>
</div>

<style>
  .calculator {
    padding: 1.5rem;
    background: var(--color-light-gray);
    margin: 2rem 0;
    max-width: 400px;
  }

  h3 {
    margin: 0 0 1rem !important;
  }

  .service {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.75rem;
    border: none;
    border-bottom: 1px solid #ddd;
    background: transparent;
    cursor: pointer;
    width: 100%;
    text-align: left;
  }

  .indicator {
    font-size: 1.25rem;
  }

  .name {
    flex: 1;
    font-weight: bold;
  }

  .price {
    color: #666;
  }

  .summary {
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
  padding-top: 1rem;
  border-top: 2px solid var(--color-dark-gray);
}

.summary-label {
  font-size: 1.125rem;
  }

.summary-amount {
  font-size: 1.125rem;
  font-weight: bold;
  color: var(--color-accent);
} 
</style>