<script>
  let count = 0
  const increment = () => {
    count += 1
  }
</script>

<h2>Counter</h2>
<button on:click={increment}>
  count is {count}
</button>
<br><br>