<script>
import svelteLogo from '../assets/svelte.svg'
</script>

<section class="container p-20 w-full">
    <div class="bg-gradient shadow-md rounded-lg py-14 bg-gradient-to-tl from-blue-400 to-green-300">
    </div>
    <div class="content mt-10">
        <h1 class="font-medium text-2xl my-4">What is kalukator?</h1>
        <p class="text-neutral-700">There are lots of Svelte project out there that aims to be learning curves for another javascript framework, and Kalukator is one of them. The creator tries to learn another language than ReactJS, Laravel, ExpressJS etc. This project is basically just to know about Svelte language, just like that. And also improving on UI/UX using pure tailwindcss. Next project will using Shadcn because i think looks cool.</p>
    </div>
    <div class="content mt-10">
        <h1 class="font-medium text-2xl my-4">Tech stack</h1>
        <p class="text-neutral-700">This is the tech stack we using.</p>
        <div class="stack-list flex gap-3 mt-4">
            <div class="card flex flex-col py-16 px-24 bg-neutral-50 rounded-xl items-center justify-center">
                <img src={svelteLogo} width={35} alt="">
                <p class="mt-2 text-xl">Svelte</p>
            </div>
        </div>
    </div>
</section>