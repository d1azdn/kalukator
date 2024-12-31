<script>
    import NoteList from "../lib/NoteList.svelte";

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

    const handleSubmit = (e) =>{
        e.preventDefault()
        tulisan = [e.target.note.value, ...tulisan]
        e.target.note.value = null

        sessionStorage.setItem('note',JSON.stringify(tulisan))
    }


</script>


<section class="container p-20 w-full">
    <div class="content mb-12">
        <form action="" onsubmit={handleSubmit} >
            <h1 class="font-medium text-2xl mb-4">Notes</h1>
            <p class="text-neutral-700 mb-4">Create notes by text here, then press 'Enter'. Right click the notes to delete them.</p>
            <input type="text" name="note" id="note" placeholder="Insert your text here" class="focus:outline-none bg-neutral-50 rounded-lg w-full ps-3 py-3 pb-14">
        </form>
    </div>

    <div class="splitter border-t border-solid border-neutral-200 my-4"></div>

    <div class="content mt-8 mb-12">
        <p class="text-neutral-700 mb-4">The notes will appear here.</p>
        <NoteList tulisan={tulisan}/>
    </div>
</section>