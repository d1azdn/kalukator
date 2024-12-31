<script>
    let expandIndex = null;
    let expandDelete = false;
    let pos = { x: 0, y: 0 }
    export let tulisan
    
    const setExpand = (index) => {
        if (expandIndex==index){
            expandIndex=null
        } else {
            expandIndex=index
        }
    }

    const handleDelete = (e) =>{
        e.preventDefault()
        tulisan.splice(expandIndex,1)
        tulisan = [...tulisan]

        sessionStorage.setItem('note',JSON.stringify(tulisan))
    }

    const handleRightClick= (e,index)=>{
        expandIndex=index
        expandDelete = true
        
        pos = {
            x: e.clientX,
            y: e.clientY
        };
        e.preventDefault()
    }
</script>

<div class="noteList flex flex-wrap gap-5">
    {#each tulisan as text, index}
    <button class={`card p-2 text-start border border-neutral-50 hover:border-neutral-300 rounded-lg min-w-32 max-w-48 min-h-14 h-full break-words ${expandIndex==index?'bg-neutral-300':'bg-neutral-50'}`} onclick={()=>{ setExpand(index) }} oncontextmenu={(e)=>handleRightClick(e,index)}>
        <p>{
            expandIndex == index ? 
            text
            :
                text.length > 100 ?
                text.slice(0,100) + "..."
                :
                text
        }</p>
    </button>
    {/each}
    {#if expandDelete}
        <button class={`delete bg-red-500 hover:bg-red-700 rounded-lg px-4 py-2 text-sm absolute text-white`} style="top:{pos.y}px; left:{pos.x}px" onclick={handleDelete}>
        Delete
        </button>
    {/if}
</div>

<svelte:window onclick={()=>expandDelete=false}/>