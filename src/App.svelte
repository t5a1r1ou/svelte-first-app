<script>
  let text = "Sevlte";
  const handleText = (event) => (text = event.target.value);

  let count = 0;
  const handleCount = (event) => (count += 1);

  let isActive = false;
  const handleActive = (event) => (isActive = !isActive);
</script>

<p>Hello {text}!</p>

<input type="text" bind:value={text} />

<input type="text" value={text} on:input={handleText} />

<input type="number" bind:value={count} />

<button on:click={handleCount}>+</button>

<button on:click={handleActive} class:active={isActive}>いいね</button>

<style>
  .active {
    background-color: #ff3e00;
    color: white;
  }
</style>
