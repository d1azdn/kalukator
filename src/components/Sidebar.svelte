<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    import svelteLogo from '../assets/svelte.svg'
    export let page

    function changePage(text){
        dispatch('setpage', text)
    }

    const pageList = {
        home : "Home",
        calculator : "Calculator",
        notes : "Notes",
        credits : "Credits"
    }
</script>


<nav class="min-w-64 bg-neutral-50 min-h-screen px-8 py-6">
    <ul class="flex flex-col">
        <li class="flex gap-4 items-center leading-relaxed text-neutral-900">
            <img src={svelteLogo} class="logo" width={20} alt="">
            <p class="font-medium text-lg">kalukator</p>
        </li>
        <li class="splitter border-t border-solid border-neutral-200 my-4"></li>
        <li class="py-1 text-sm font-medium leading-relaxed text-neutral-950">Pages</li>
        {#each Object.entries(pageList) as [key,index]}
            <li><button onclick={()=>changePage(key)} class={`py-1 text-sm font-medium leading-relaxed w-full text-start ${page== key ? 'text-purple-800':'text-neutral-500 hover:text-purple-800' }`}>{index}</button></li>
        {/each}
    </ul>
</nav>