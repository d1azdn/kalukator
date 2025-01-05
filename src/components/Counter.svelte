<script>
import NavigationBar from "../lib/NavigationBar.svelte";
import CounterButton from "../lib/CounterButton.svelte";
</script>

<section class="container w-full flex justify-between">
    <div class="p-20 w-full">    
        <div class="header">
            <h1 class="headerTitle">Counter</h1>
        </div>

        <div class="content">
            <h1 class="title" id="introduction">Introduction</h1>
            <p class="text">
                A counter is a mechanism, device, or code implementation used to keep track of occurrences, events, or values by incrementing or decrementing numbers systematically. In programming, a counter is often a variable initialized to a specific value (commonly zero) and adjusted as events occur, such as clicks on a button or iterations in a loop. Counters can be found in various applications, from hardware devices like digital clocks and step trackers to software systems like page visit counters or task progress monitors.</p>
        </div>

        <div class="content">
            <h1 class="title" id="history">History</h1>
            <p class="text">None</p>
        </div>

        <div class="content">
            <h1 class="title" id="codeflow">Code flow</h1>
            <p class="text">
            This code used svelte <b class="boldtext">Reactivity</b>, that uses no additional <b class="boldtext">setState or useEffect</b> required.
            </p>
            <p class="textmulti">
                <i class="italic">// the code looks like this</i>
                <br>
                let count = 0

                function increment ()&#123
                    count += 1
                &#125
            </p>
        </div>

        <div class="content end">
            <h1 class="title" id="testing">Testing</h1>
            <CounterButton/>
        </div>

    </div>

    <NavigationBar />
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
    .boldtext{
        @apply p-2 bg-neutral-50
    }
</style>