<script>
export let titleList
    
const handleClick = (id) => {
        const offset = 45
        const target = document.getElementById(id)
        const elementPosition = target.getBoundingClientRect().top + window.scrollY;

        window.scrollTo({
        top: elementPosition - offset,
        behavior: 'smooth', // Smooth scrolling effect
        })
    }
</script>

<div class="me-10 my-20 min-w-52 h-screen">
    <div class="fixed border-l border-solid border-neutral-200 py-1 ps-4 ">
        <h1 class="font-semibold">On this page</h1>
        <div class="flex flex-col">
        {#each Object.entries(titleList) as [key,index]}
            <button class="text-neutral-500 text-sm py-1 text-start hover:text-purple-800" onclick={()=>handleClick(index.id)}>{index.title}</button>
        {/each}
        </div>
    </div>
</div>