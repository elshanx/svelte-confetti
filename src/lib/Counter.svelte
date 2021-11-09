<script lang="ts">
  import Confetti from './Confetti.svelte'

  let count: number = 0
  const increment = () => count++
  let intervalId: NodeJS.Timer | undefined = undefined

  const toggleInterval = () => {
    if (intervalId) {
      clearInterval(intervalId)
      intervalId = null
    } else intervalId = setInterval(increment, 75)
  }
  const reportBugClick = () =>
    void (window.location.href = 'https://www.youtube.com/watch?v=dQw4w9WgXcQ')
</script>

<section>
  <header>
    <button on:click={toggleInterval}>set interval</button>
    <button on:click={reportBugClick}>report a bug</button>
  </header>
  <div class="btn-wrapper">
    {#if count >= 10}
      <div class="confetti">
        <Confetti timeout={5000} />
      </div>
    {/if}
    <button on:click={increment}> Clicks: {count}</button>
  </div>
</section>

<style>
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  section {
    padding: 1.4rem;
    position: relative;
    height: 100%;
  }
  .btn-wrapper {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  .btn-wrapper button {
    width: 500px;
    height: 170px;
    font-size: 66px;
    border-width: 3px;
  }
  .confetti {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
  }
  button {
    cursor: pointer;
    background: inherit;
    color: #cf4517;
    padding: 8px 14px;
    border: 1px solid #cf4517;
    font-size: 18px;
    text-transform: capitalize;
    transition: all 220ms ease-in;
  }
  button:hover {
    filter: invert(1);
  }
  button:focus {
  }

  button:active {
  }
</style>
