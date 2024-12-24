<script>
  let count = $state("")
  const increment = () => {
    count += 1
  }
</script>

<button onclick={increment}>
  count is {count} and that is
</button>
