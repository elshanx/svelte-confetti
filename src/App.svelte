<script lang="ts">
  import Counter from './lib/Counter.svelte'
</script>

<main>
  <Counter />
</main>

<style>
  :global(*, *::before, *::after) {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  :global(body) {
    width: 100%;
    height: 100%;
    background: #11111c;
  }
  main {
    height: 100vh;
  }
</style>
