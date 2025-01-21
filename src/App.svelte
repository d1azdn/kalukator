<script>
  import Sidebar from './components/Sidebar.svelte';
  import Home from './components/Home.svelte';
  import Calculator from './components/Calculator.svelte';
  import Notes from './components/Notes.svelte';
  import Counter from './components/Counter.svelte';
  import Credits from './components/Credits.svelte';
  let page = 'home'

  function changePage(e){
    page = e.detail
    sessionStorage.setItem('page',e.detail)
  }

  if (!sessionStorage.getItem('page')){
    sessionStorage.setItem('page','home')
  } else {
    page = sessionStorage.getItem('page')
  }
</script>

<main class="flex flex-row">
  <Sidebar page={page} on:setpage={changePage}/>
  {#if page=='home'}
    <Home on:setpage={changePage}/>
  {:else if page=='calculator'}
    <Calculator on:setpage={changePage}/>
  {:else if page=='notes'}
    <Notes/>
  {:else if page=='counter'}
    <Counter/>
  {:else}
    <Credits/>
  {/if}
</main>
