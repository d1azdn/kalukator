<script>
    import NavigationBar from "../lib/NavigationBar.svelte";
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


<section class="container w-full flex justify-between">
    <div class="p-20 w-full">    
        <div class="header">
            <h1 class="headerTitle">Notes</h1>
        </div>

        <div class="content">
            <h1 class="title" id="introduction">Introduction</h1>
            <p class="text">
            The term "notes" has various meanings depending on the context. It can refer to brief records or points written to aid memory, such as during a lecture or meeting, or to symbols in musical notation that represent pitch, duration, and rhythm. Notes can also mean annotations or comments added to texts for clarification, or even paper money, such as a $20 note. Additionally, the word can describe a general tone, mood, or impression, such as ending a speech on a positive note.</p>
        </div>

        <div class="content">
            <h1 class="title" id="history">History</h1>
            <p class="text">
            Record-keeping (or Notes) has been an integral part of human history since ancient civilizations. The Sumerians in Mesopotamia (~3100 BCE) used cuneiform on clay tablets to document trade and religious rituals, while the Egyptians inscribed hieroglyphs on papyrus.</p>
            <p class="text">
            In China (~1200 BCE), early records were found on oracle bones, and the invention of paper by the Han Dynasty replaced materials like bamboo. In India, palm leaves were used to preserve religious texts such as the Vedas, whereas the Greeks and Romans employed parchment scrolls and wax tablets for laws and literature. During the medieval era, churches preserved records through manuscripts, leading to innovations like paper and printing that revolutionized the dissemination of knowledge globally.</p>
        </div>

        <div class="content">
            <h1 class="title" id="codeflow">Code flow</h1>
            <p class="text">
            This code used <b class="boldtext">sessionStorage()</b> to store the data from the form when submitted. 
            </p>
        </div>

        <div class="content end">
            <form action="" onsubmit={handleSubmit} >
                <h1 class="title" id="notes">Add notes</h1>
                <p class="text">Create notes by text here, then press 'Enter'. Right click the notes to delete them.</p>
                <input type="text" name="note" id="note" placeholder="Insert your text here" class="focus:outline-none bg-neutral-50 rounded-lg w-full ps-3 py-3 pb-14">
            </form>
            <p class="text">The notes will appear here.</p>
            <NoteList tulisan={tulisan}/>
        </div>

    </div>

    <NavigationBar />
</section>

<style>
    .header{
        @apply pb-12 border-b border-solid border-neutral-200
    }
    .headerTitle{
        @apply font-medium text-4xl
    }
    .content{
        @apply pt-8 pb-12 border-b border-solid border-neutral-200
    }
    .content.end{
        @apply pt-8 pb-12 border-none
    }
    .content .title{
        @apply font-medium text-2xl mb-4
    }
    .content .text{
        @apply text-neutral-600 my-4
    }
    .content .text .link{
        @apply text-blue-500 hover:underline
    }
    .boldtext{
        @apply p-2 bg-neutral-50
    }
</style>