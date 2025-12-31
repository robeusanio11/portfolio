<script setup>
</script>

<template>
    <div class="about-container">
        <div class="about-cards">
            <img class="image-card" src="/LOLstats1.PNG" alt="Robert Eusanio Headshot" />
            <div class="card">
                <h5>Education</h5>
                <p>CSU - Stanislaus</p>
            </div>
            <div class="card">
                <h5>Contact Info</h5>
                <p>Email: robeusanio11@gmail.com</p>
                <p>Phone: (209) 814-7968</p>
            </div>
            <div class="card">
                <h5>Location</h5>
                <p>Tracy, California (Open to relocation)</p>
            </div>
        </div>
        <div class="about-info">
            <h2>About Me</h2>
            <p>My name is Rob and this is about me.</p>
        </div>
    </div>
</template>

<style scoped>
    .about-container {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        width: 100%;
        background-color: lightblue
    }

    .about-container > div {
        border-style: solid;
        padding: 1rem;
        margin: 1rem;
        width: 100%;
    }

    .about-cards {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .card {
        padding: 0.5rem;
        margin: 0.5rem;
        border-style: solid;
        width: 60%;
        border-radius: 20px;

        transition: 
            width 0.2s ease,
            padding 0.2s ease,
            border-color 0.2s ease
    }

    .card:hover {
        border-color: blue;
        width: 65%;
        padding: 1rem;
    }

    .card > * {
        margin: 0 auto;
    }

    img {
        width: 25rem;
        height: 25rem;
        margin: 1rem;
        border-style: solid;
    }

</style>