<script lang="ts">
    import { onMount } from "svelte";
    import Msdate from "../msdate.svelte";

    let date: string | undefined;

    onMount(() => {
        date = document.getElementById("date").textContent;
    });
</script>

<style>
    :root {
        font-size: 2vmax;
    }

    * {
        font-family: "Oswald", sans-serif;
        color: white;
    }

    main {
        text-align: center;
    }

    div.separator {
        display: block;
        width: 80%;
        margin: 0.5rem auto;
        height: calc(1rem / 8);
        background-color: #a5b1c2;
    }

    footer {
        opacity: 0.6;
        transition: opacity 0.5s ease-in-out;
        text-align: center;
        margin-top: 2rem;
    }

    footer:hover {
        opacity: 1;
    }

    h3 {
        font-weight: 300;
        font-size: 2rem;
        padding: 0;
        margin: 0;
    }

    h1 {
        font-weight: 700;
        font-size: 3rem;
        padding: 0;
        margin: 0;
    }

    a, a:focus, a:visited {
        color: #fd9644;
    }
</style>

<svelte:head>
    <title>{date ? `${date} | ` : ""}Get your current date in Microsoft Exchange era</title>
    <link rel="preconnect" href="https://fonts.googleapis.com"/>
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
    <link href="https://fonts.googleapis.com/css2?family=Oswald:wght@300;700&display=swap" rel="stylesheet"/> 
</svelte:head>
 
<main>
    <h3>Hello, today's date is</h3>
    <h1 id="date"><Msdate></Msdate></h1>
    <h3>according to the Microsoft Exchange era.</h3>

    <!-- Wayback Machine link, in case the support page gets updated. -->
    <!-- https://web.archive.org/web/20220102235702/https://techcommunity.microsoft.com/t5/exchange-team-blog/email-stuck-in-exchange-on-premises-transport-queues/ba-p/3049447 -->

    <footer>
        This obvious joke originates from a <a href="https://techcommunity.microsoft.com/t5/exchange-team-blog/email-stuck-in-exchange-on-premises-transport-queues/ba-p/3049447" rel="noopener nofollow" target="_blank">bugfix</a>, Microsoft introduced to fix the <a href="https://en.wikipedia.org/wiki/Time_formatting_and_storage_bugs#Year_2022" rel="noopener nofollow" target="_blank">Y2K22 bug</a>.

        <div class="separator"></div>

        <a href="https://github.com/RicoBrase/microsoftdate.today" rel="noopener nofollow" target="_blank">Find this project on GitHub</a>
    </footer>
</main>

