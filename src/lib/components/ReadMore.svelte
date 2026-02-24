<script>
  let { title, children } = $props();
  let isExpanded = $state(false);
</script>

<div class="read-more">
  <button onclick={() => isExpanded = !isExpanded}>
    {isExpanded ? '▼' : '▶'} {title}
  </button>
  {#if isExpanded}
    <div class="content">
      {@render children()}
    </div>
  {/if}
</div>

<style>
  .read-more {
    margin: 1.5rem 0;
    border: 1px solid var(--color-light-gray);
  }

  button {
    width: 100%;
    padding: 1rem;
    text-align: left;
    background: var(--color-light-gray);
    border: none;
    font-weight: bold;
    cursor: pointer;
  }

  .content {
    padding: 1rem;
    border-top: 1px solid var(--color-light-gray);
  }
</style>