<script>
    import { leagueName } from '$lib/utils/helper';
    import { fade } from 'svelte/transition'; // Import the fade transition
    import ManagerRow from './ManagerRow.svelte';

    export let managers, leagueTeamManagers;

    let innerWidth;
    let currentManagerIndex = 0;  // State variable for carousel position

    function nextManager() {
        if (currentManagerIndex < managers.length - 1) {
            currentManagerIndex++;
        } else {
            currentManagerIndex = 0;  // Loop back to the first item
        }
    }

    function previousManager() {
        if (currentManagerIndex > 0) {
            currentManagerIndex--;
        } else {
            currentManagerIndex = managers.length - 1;  // Loop back to the last item
        }
    }
</script>

<svelte:window bind:innerWidth={innerWidth} />

<style>
    /* Utilizing modern fonts for a sleek appearance */
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

    /* Base styles for better default looks */
    h2 {
        font-family: 'Poppins', sans-serif;
        color: #333; /* Soft black for text */
    }

    /* Container for the managers with added padding and shadow for depth */
    .managerContainer {
        width: 100%;
        margin: 4em 0;
        padding: 2em;
        background-color: #f9f9f9; /* Soft light gray for subtle depth */
        border-radius: 10px;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05); /* Gentle shadow */
    }

    /* Centralized content with a max-width for better reading */
    .managerConstrained {
        width: 97%;
        max-width: 800px;
        margin: 0 auto;
        padding: 2em;
        background-color: #fff; /* Pure white for contrast */
        border-radius: 10px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1); /* Light shadow for depth */
    }

    /* Titles styles */
    h2 {
        text-align: center;
        font-size: 2.4em;
        margin-bottom: 2em;
        letter-spacing: -0.8px; /* Tighten the letter spacing for modern feel */
    }

    @media (max-width: 520px) {
        h2 {
            font-size: 1.8em;
            margin: 1.5em 0 1em;
        }
    }

    /* Button styling with hover transition */
    .carouselBtn {
        background-color: #007BFF; /* Vibrant blue for a modern touch */
        border: none;
        padding: 12px 24px;
        margin: 10px;
        cursor: pointer;
        color: #ffffff; /* White text for contrast */
        border-radius: 5px;
        transition: background-color 0.3s ease, transform 0.2s ease; /* Smooth transitions */
    }

    .carouselBtn:hover {
        background-color: #0056b3; /* Darken on hover */
        transform: scale(1.05); /* Slightly increase size for a dynamic feel */
    }
</style>


<div class="managerContainer">
    <h2>{leagueName} Managers</h2>
    <div class="managerConstrained">
        <!-- Wrap ManagerRow in a div and apply the fade transition to that div -->
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