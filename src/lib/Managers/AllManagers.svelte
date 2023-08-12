<script>
    import { leagueName } from '$lib/utils/helper';
    import { fade } from 'svelte/transition'; // Import the fade transition
    import ManagerRow from './ManagerRow.svelte';

    let managers, leagueTeamManagers;

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

h2 {
    font-family: 'Poppins', sans-serif;
    color: #333; /* Soft black for text */
    text-align: center;
    font-size: 1.6em;
    margin-bottom: 1em;
    letter-spacing: -0.6px;
}

.managerContainer {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 1em; /* Added padding to ensure content doesn't touch screen edges */
}

.managerItem {
    flex: 1 1 calc(100% - 20px); /* Full width for mobile by default */
    margin: 10px;
    padding: 15px; /* Reduced padding */
    background-color: #fff;
    border-radius: 7px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    text-align: center;
}

img {
    max-width: 100%; /* Ensuring images don't break layout */
    border-radius: 5px; /* Optional, for some styling */
    margin-bottom: 10px; /* Reduced margin */
}

h3 {
    margin-bottom: 8px;
    font-size: 1.3em; /* Adjusted size */
    color: #007BFF; /* Giving color to manager name for some contrast */
}

.carouselBtn {
    background-color: #007BFF; 
    border: none;
    padding: 8px 16px; /* Reduced padding for mobile */
    margin-top: 8px;
    cursor: pointer;
    color: #ffffff; 
    border-radius: 5px;
    transition: background-color 0.3s ease, transform 0.2s ease; 
}

.carouselBtn:hover {
    background-color: #0056b3;
    transform: scale(1.03);
}

/* Adjustments for bigger screens (tablets onwards) */
@media (min-width: 521px) {
    .managerItem {
        flex: 1 1 calc(50% - 20px); /* 2 items per row on larger screens */
    }

    h2 {
        font-size: 2em;
        margin: 1.5em 0 1em;
    }

    h3 {
        font-size: 1.5em;
    }
}

/* Adjustments for desktop screens */
@media (min-width: 800px) {
    .managerItem {
        flex: 1 1 calc(33.333% - 20px); /* 3 items per row on desktop */
    }

    h2 {
        font-size: 2.4em;
        margin-bottom: 2em;
    }
}

</style>



<div class="managerContainer">
    <h2>RIFF</h2>

    <!-- Manager Row Item -->
    <div class="managerItem">
        <div class="managerConstrained">
            {#each managers as manager, key}
                <ManagerRow {manager} {leagueTeamManagers} {key} />
            {/each}
        </div>
        <!-- svelte-ignore a11y-img-redundant-alt -->
        <img src="managerImage.jpg" alt="Manager Image" />
        <h3>Manager Name</h3>
        <p>Some details about the manager.</p>
        <button class="carouselBtn">View More</button>
    </div>
</div>

<div class="managerContainer">
    <h2>MIGZ</h2>

    <!-- Manager Row Item -->
    <div class="managerItem">
        <div class="managerConstrained">
            {#each managers as manager, key}
                <ManagerRow {manager} {leagueTeamManagers} {key} />
            {/each}
        </div>
        <!-- svelte-ignore a11y-img-redundant-alt -->
        <img src="managerImage.jpg" alt="Manager Image" />
        <h3>Manager Name</h3>
        <p>Some details about the manager.</p>
        <button class="carouselBtn">View More</button>
    </div>

    <!-- Repeat the above "managerItem" div for each manager -->
</div>


<div class="managerContainer">
    <h2>ANGEL</h2>

    <!-- Manager Row Item -->
    <div class="managerItem">
        <div class="managerConstrained">
            {#each managers as manager, key}
                <ManagerRow {manager} {leagueTeamManagers} {key} />
            {/each}
        </div>        
        <!-- svelte-ignore a11y-img-redundant-alt -->
        <img src="managerImage.jpg" alt="Manager Image" />
        <h3>Manager Name</h3>
        <p>Some details about the manager.</p>
        <button class="carouselBtn">View More</button>
    </div>

    <!-- Repeat the above "managerItem" div for each manager -->
</div>