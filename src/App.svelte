<script>
  // import svelteLogo from './assets/svelte.svg'
  // import viteLogo from '/vite.svg'
  // import Counter from './lib/Counter.svelte'
  import Sidebar from './components/Sidebar.svelte';
  import Home from './components/Home.svelte';
  import Notes from './components/Notes.svelte';
    import Calculator from './components/Calculator.svelte';
    import Credits from './components/Credits.svelte';
  let page = 'notes'

  function changePage(e){
    page = e.detail
  }
</script>

<main class="flex flex-row">
  <Sidebar page={page} on:setpage={changePage}/>
  {#if page=='home'}
  <Home/>
  {:else if page=='calculator'}
  <Calculator/>
  {:else if page=='notes'}
  <Notes/>
  {:else}
  <Credits/>
  {/if}
</main>
