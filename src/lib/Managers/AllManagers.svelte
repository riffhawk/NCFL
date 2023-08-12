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
    }

    .managerContainer {
        /* ... existing styles ... */
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }

    .managerItem {
        flex: 1 1 calc(33.333% - 20px); /* Taking up roughly a third, minus margins for space */
        margin: 10px;
        padding: 20px;
        background-color: #fff;
        border-radius: 10px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        text-align: center;
    }

    img {
        max-width: 100%; /* Ensuring images don't break layout */
        border-radius: 5px; /* Optional, for some styling */
        margin-bottom: 15px;
    }

    h3 {
        margin-bottom: 10px;
        color: #007BFF; /* Giving color to manager name for some contrast */
    }

    /* Adjusting for smaller screens */
    @media (max-width: 520px) {
        .managerItem {
            flex: 1 1 100%; /* On smaller screens, manager item will take full width */
        }
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
        margin-top: 10px;
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
    <h2>RIFF</h2>

    <!-- Manager Row Item -->
    <div class="managerItem">
        <!-- Manager content goes here. For instance: -->
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
        <!-- Manager content goes here. For instance: -->
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
        <!-- Manager content goes here. For instance: -->
        <!-- svelte-ignore a11y-img-redundant-alt -->
        <img src="managerImage.jpg" alt="Manager Image" />
        <h3>Manager Name</h3>
        <p>Some details about the manager.</p>
        <button class="carouselBtn">View More</button>
    </div>

    <!-- Repeat the above "managerItem" div for each manager -->
</div>