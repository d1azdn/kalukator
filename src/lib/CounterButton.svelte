<script>
  let count = 0
  const increment = () => {
    count += 1
  }
  const reset = () => {
    count = 0
  }
</script>

<div class="counter flex flex-col bg-neutral-50 p-10 items-center justify-start rounded-lg">
  <h1>Counter : {count}</h1>
  <div class="button">
    <button onclick={reset} class="border border-solid w-32 p-1 bg-white rounded-xl hover:bg-neutral-100">
      Reset
    </button>
    <button onclick={increment} class="w-32 p-1 bg-neutral-200 hover:bg-neutral-300 rounded-xl">
      Click me!
    </button>
  </div>
</div>
    