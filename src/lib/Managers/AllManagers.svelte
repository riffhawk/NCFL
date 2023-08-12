<script>
    import { leagueName } from '$lib/utils/helper';
    import { fade } from 'svelte/transition'; 
    import ManagerRow from './ManagerRow.svelte';

    export let managers, leagueTeamManagers;

    let innerWidth;
    let currentManagerIndex = 0;

    function nextManager() {
        if (currentManagerIndex < managers.length - 1) {
            currentManagerIndex++;
        } else {
            currentManagerIndex = 0; 
        }
    }

    function previousManager() {
        if (currentManagerIndex > 0) {
            currentManagerIndex--;
        } else {
            currentManagerIndex = managers.length - 1; 
        }
    }
</script>

<svelte:window bind:innerWidth={innerWidth} />

<style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');
    @import 'skeleton-css/skeleton.css'; /* Import Skeleton styles */

    h2 {
        font-family: 'Poppins', sans-serif;
        color: #333;
    }

    .managerContainer {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 4em 0;
        padding: 2em;
        background-color: #f9f9f9;
        border-radius: 10px;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
    }

    .managerConstrained {
        width: 97%;
        max-width: 800px;
        padding: 2em;
        background-color: #fff;
        border-radius: 10px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    }

    h2 {
        text-align: center;
        font-size: 2.4em;
        margin-bottom: 2em;
        letter-spacing: -0.8px;
    }

    @media (max-width: 520px) {
        h2 {
            font-size: 1.8em;
            margin: 1.5em 0 1em;
        }
    }

    .carouselBtn {
        background-color: #007BFF;
        border: none;
        padding: 12px 24px;
        margin: 10px;
        cursor: pointer;
        color: #ffffff;
        border-radius: 5px;
        transition: background-color 0.3s ease, transform 0.2s ease;
    }

    .carouselBtn:hover {
        background-color: #0056b3;
        transform: scale(1.05);
    }
</style>

<div class="managerContainer">
    <h2>{leagueName} Managers</h2>
    <div class="managerConstrained">
        <div in:fade={{ duration: 500 }}>
            <ManagerRow 
                manager={managers[currentManagerIndex]} 
                leagueTeamManagers={leagueTeamManagers} 
                key={currentManagerIndex} />
        </div>
        
        <button class="carouselBtn" on:click={previousManager}>Previous</button>
        <button class="carouselBtn" on:click={nextManager}>Next</button>
    </div>
</div>
