<script>
    import NavigationBar from "../lib/NavigationBar.svelte";
</script>

<section class="container w-full flex justify-between">
    <div class="p-20 w-full">  
        <div class="header">
            <h1 class="headerTitle">Credits</h1>
        </div>
        <div class="content">
            <h1 class="title" id="credits">You are</h1>
            <p class="text">Thank you so much for taking the time to check out this project. It might not be the most impressive out there, but I really enjoy working on projects like this.</p>
            <p class="text">Additionally, sincere thanks to all the developers, contributors, and communities behind the open-source libraries, tools, and resources that supported this project. Your work is invaluable and deeply appreciated.</p>
        </div>

        <div class="content end">
            <h1 class="title" id="again">Awesome</h1>
            <p class="text">This project was made possible thanks to the following tools, frameworks, and technologies:</p>
            <p class="textmulti">
                Visual Studio Code
                Svelte
                Stackoverflow
                ChatGPT
            </p>
        </div>
    </div>

    <NavigationBar/>
</section>

<style lang="postcss">
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
    .content .textmulti{
        @apply text-neutral-600 whitespace-pre-line bg-neutral-50 p-2 rounded-lg
    }
</style>