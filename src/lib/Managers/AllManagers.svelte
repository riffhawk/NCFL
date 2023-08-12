<script>
    import { leagueName } from '$lib/utils/helper';
    import { fade } from 'svelte/transition';
    import ManagerRow from './ManagerRow.svelte';

    export let managers = [];
    export let leagueTeamManagers;

    let innerWidth;
    let currentManagerIndex = 0;

    function nextManager() {
        if (managers && currentManagerIndex < managers.length - 1) {
            currentManagerIndex++;
        } else {
            currentManagerIndex = 0; 
        }
    }

    function previousManager() {
        if (managers && currentManagerIndex > 0) {
            currentManagerIndex--;
        } else if (managers) {
            currentManagerIndex = managers.length - 1; 
        }
    }
</script>

<svelte:window bind:innerWidth={innerWidth} />

<style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;700&display=swap');



    .managerContainer {
        max-width: 900px;
        width: 90%; /* a bit of responsiveness */
        margin: 2em auto;
        padding: 2em;
        background-color: #ffffff;
        border-radius: 12px;
        box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
    }

    h2 {
        text-align: center;
        font-weight: 700;
        font-size: 2rem;
        margin-bottom: 1.5em;
        color: #007BFF;
    }

    @media (max-width: 520px) {
        h2 {
            font-size: 1.6rem;
            margin-bottom: 1em;
        }
    }

    .carouselBtn {
        background-color: #007BFF;
        border: none;
        padding: 10px 20px;
        margin: 10px;
        cursor: pointer;
        color: #ffffff;
        border-radius: 8px;
        font-weight: 500;
        transition: background-color 0.3s, transform 0.2s;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }

    .carouselBtn:hover, .carouselBtn:focus {
        background-color: #0056b3;
        transform: scale(1.05);
    }

    .btnContainer {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 20px;
        margin-top: 20px;
    }
</style>

<div class="managerContainer">
    <h2>{leagueName} Managers</h2>
    
    <div in:fade={{ duration: 300 }}>
        <!-- Remember to handle the fallback image scenario in ManagerRow component! -->
        <ManagerRow 
            manager={managers[currentManagerIndex]} 
            leagueTeamManagers={leagueTeamManagers} 
            key={currentManagerIndex} />
    </div>

    <div class="btnContainer">
        <button class="carouselBtn" on:click={previousManager}>← Previous</button>
        <button class="carouselBtn" on:click={nextManager}>Next →</button>
    </div>
</div>
