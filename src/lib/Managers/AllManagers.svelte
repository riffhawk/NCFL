<script>
    import { leagueName } from '$lib/utils/helper';
    import ManagerRow from './ManagerRow.svelte';

    export let managers, leagueTeamManagers;

    let innerWidth;
</script>

<svelte:window bind:innerWidth={innerWidth} />

<style>
    /* Using Roboto as an example; ensure it's available or replace with another font */
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

    body, h2 {
        font-family: 'Roboto', sans-serif;
    }

    .managerContainer {
        width: 100%;
        margin: 4em 0;
        background-color: #f9f9f9; /* Light grayish background for a subtle difference */
        padding: 2em;
        border-radius: 8px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1); /* Subtle shadow */
    }

    .managerConstrained {
        width: 97%;
        max-width: 800px;
        margin: 0 auto;
        padding: 2em;
        background-color: #fff;
        border-radius: 8px;
    }

    h2 {
        text-align: center;
        font-size: 2.8em;
        margin-bottom: 2em;
        color: #333; /* Darker text for better readability */
    }

    @media (max-width: 520px) {
        h2 {
            font-size: 2em;
            margin: 1.5em 0 1em;
        }
    }

    /* Enhancing the buttons */
    .carouselBtn {
        background-color: #007BFF; /* A vibrant blue */
        border: none;
        padding: 10px 20px;
        margin: 10px;
        cursor: pointer;
        color: white; /* Text color */
        border-radius: 4px;
        transition: background-color 0.3s ease; /* Transition effect */
    }

    .carouselBtn:hover {
        background-color: #0056b3; /* A darker blue on hover */
    }
</style>

<div class="managerContainer">
    <h2>{leagueName} Managers</h2>
    <div class="managerConstrained">
        {#each managers as manager, key}
            <ManagerRow {manager} {leagueTeamManagers} {key} />
        {/each}
    </div>
</div>
