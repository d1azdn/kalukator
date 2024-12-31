<script>
    import NavigationBar from '../lib/NavigationBar.svelte';
    import svelteLogo from '../assets/svelte.svg'
    import { onMount } from 'svelte';
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    let titleList = []

    function changePage(text){
        dispatch('setpage', text)
    }

    onMount(()=>{
        const getTitle = document.getElementsByClassName('title')
        titleList = Array.from(getTitle).map(value=>{
            return {
                id : value.id,     
                title : value.textContent
            }
        })
        console.log(titleList)
    })

</script>

<section class="container w-full flex">
    <div class="p-20">
        <div class="header">
            <h1 class="headerTitle">Kalukator</h1>
        </div>
        <div class="content">
            <h1 class="title" id="overview">Overview</h1>
            <p class="text">
                There are plenty of Svelte projects out there designed to help people learn a new JavaScript framework, and Kalukator is one of them. The creator wanted to explore something beyond ReactJS, Laravel, and ExpressJS. 
            </p>
            <p class="text">
                This project is essentially a way to get familiar with Svelte, plain and simple. Additionally, it's an opportunity to improve UI/UX using pure TailwindCSS.
            </p>
            <p class="text">
                This project also available on github, check it out <a href="https://github.com/d1azdn/kalukator" target="_blank" class="link">here</a>.
            </p>
        </div>

        <div class="content">
            <h1 class="title" id="features">Features</h1>
            <p class="text">
                This project initially started as a simple experiment with Svelte, without any specific focus or real-world project examples. Besides that, there are several features you can try out.
            </p>
            <p class="text">
                For the feature there are 
                <button class="link" onclick={()=>{changePage('calculator')}}>Calculator</button>, 
                <button class="link" onclick={()=>{changePage('notes')}}>Notes</button>, 
                <button class="link" onclick={()=>{changePage('counter')}}>Counter</button> 
                that you can explore by clicking!
            </p>
        </div>
        
        <div class="content end">
            <h1 class="title" id="techstack">Tech stack</h1>
            <p class="text">This is the tech stack that was used.</p>
            <div class="stack-list flex gap-3 mt-4">
                <div class="card flex flex-col py-16 px-24 bg-neutral-50 rounded-xl items-center justify-center">
                    <img src={svelteLogo} width={35} alt="">
                    <p class="mt-2 text-xl">Svelte</p>
                </div>
            </div>
        </div>

    </div>

    <NavigationBar titleList={titleList}/>

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
</style>