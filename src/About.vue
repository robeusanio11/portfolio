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
            
        </div>
    </div>
</template>

<style scoped>
    .about-container {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }

    .about-container > div {
        border-style: solid;
        padding: 1rem;
        margin: 1rem;
    }

    .about-cards {
        display: flex;
        flex-direction: column;
        /* justify-content: center;
        align-items: center; */
    }

    .about-cards > div {
        padding: 0.5rem;
        margin: 0.5rem;
        border-style: solid;
        width: 90%;
    }

    .card > * {
        margin: 0 auto;
    }

    img {
        width: 25rem;
        height: 25rem;
        margin: 1rem;
    }

</style>