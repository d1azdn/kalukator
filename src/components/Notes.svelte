<script>
    let pos = { x: 0, y: 0 }

    let tulisan = [
        "halo semua",
        "salam kenal",
    ]

    if (!sessionStorage.getItem('note')){
        sessionStorage.setItem('note','')
    } else {
        const dataTulisan = JSON.parse(sessionStorage.getItem('note'))
        tulisan = [...dataTulisan]
    }

    let expandIndex = null;
    let expandDelete = false;

    const setExpand = (index) => {
        if (expandIndex==index){
            expandIndex=null
        } else {
            expandIndex=index
        }
    }

    const handleSubmit = (e) =>{
        e.preventDefault()
        tulisan = [e.target.note.value, ...tulisan]
        e.target.note.value = null

        sessionStorage.setItem('note',JSON.stringify(tulisan))
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


<section class="container p-20 w-full">
    <div class="content">
        <form action="" onsubmit={handleSubmit} >
            <h1 class="font-medium text-2xl my-4">Notes</h1>
            <input type="text" name="note" id="note" placeholder="Insert your text here" class="focus:outline-none w-full pb-10">
        </form>
    </div>

    <div class="splitter border-t border-solid border-neutral-200 my-4"></div>

    <div class="content mt-10 flex flex-wrap gap-5">
        {#each tulisan as text, index}
        <button class={`card p-2 bg-neutral-50 text-start border border-neutral-50 hover:border-neutral-300 rounded-lg min-w-32 max-w-48 min-h-14 h-full break-words`} onclick={()=>{ setExpand(index) }} oncontextmenu={(e)=>handleRightClick(e,index)}>
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
</section>

<svelte:window onclick={()=>expandDelete=false}/>