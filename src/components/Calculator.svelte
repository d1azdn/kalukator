<script>
import NavigationBar from "../lib/NavigationBar.svelte";

import { createEventDispatcher } from 'svelte';
const dispatch = createEventDispatcher();

let num1 = 0
let num2 = 0
let method = "multiple"
let result = 0

$: result = calculate(num1,num2,method);

function changePage(text){
    dispatch('setpage', text)
}

function calculate(num1,num2,method){
    if (method == "multiple"){
        return num1*num2
    }
    if (method == "divide"){
        return num1/num2
    }
    if (method == "add"){
        return num1+num2
    }
    if (method == "subtract"){
        return num1-num2
    }

}
</script>

<section class="container w-full flex justify-between">
    <div class="p-20 w-full">    
        <div class="header">
            <h1 class="headerTitle">Calculator</h1>
            <p class="text">Not to be confused with the actual home site <button class="link" onclick={()=>{changePage('home')}}>Kalukator</button></p>
        </div>

        <div class="content">
            <h1 class="title" id="introduction">Introduction</h1>
            <p class="text">
                A calculator is an electronic or mechanical device designed to perform mathematical operations quickly and accurately. It ranges from basic models that handle simple arithmetic like addition, subtraction, multiplication, and division to advanced scientific or graphing calculators capable of solving complex equations, plotting graphs, and performing statistical analyses. Modern calculators are compact and portable, often powered by batteries or solar energy, and are commonly used in education, business, engineering, and daily life. </p>
        </div>

        <div class="content">
            <h1 class="title" id="history">History</h1>
            <p class="text">The history of the calculator began with the abacus, developed around 2000 BCE for basic arithmetic. In the 17th century, mechanical devices like Pascal`s "Pascaline" and Leibniz`s "Stepped Reckoner" advanced calculations. The 20th century introduced electronic calculators, evolving from bulky machines to pocket-sized devices with microchip technology. Today, calculators are integrated into smartphones and computers, showcasing their lasting significance.</p>
        </div>

        <div class="content">
            <h1 class="title" id="codeflow">Code flow</h1>
            <p class="text">
            This code used svelte <b class="boldtext">Reactivity</b>, that uses no additional <b class="boldtext">setState or useEffect</b> required.
            </p>
            <p class="textmulti">
                <i class="italic">// the code looks like this</i>
                <br>
                let num1 = 0
                let num2 = 0

                $: result = calculate(num1,num2,method);
            </p>
        </div>

        <div class="content end">
            <h1 class="title" id="testing">Testing</h1>
            <form action="">
                <input type="number" name="" id="" class="border border-solid px-2" placeholder="Insert number here" bind:value={num1}>
                <select name="" id="" bind:value={method}>
                    <option value="multiple">multiple by</option>
                    <option value="divide">divide by</option>
                    <option value="add">add by</option>
                    <option value="subtract">subtract by</option>
                </select>
                <input type="number" name="" id="" class="border border-solid px-2" placeholder="Insert number here" bind:value={num2}>
            </form>
            <p class="mt-2">Logic : {num1} {method} by {num2} is {result}</p>
        </div>

    </div>

    <NavigationBar />
</section>

<style lang="postcss">
    .header{
        @apply pb-12 border-b border-solid border-neutral-200
    }
    .header .text .link{
        @apply text-blue-500 hover:underline italic
    }
    .header .text{
        @apply italic
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
    .boldtext{
        @apply p-2 bg-neutral-50
    }

</style>