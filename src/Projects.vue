<script setup>
</script>

<template>
    <div class="projects-section">
        <div class="project-info-container">
            <h1 class="project-title">Title</h1>
            <p>Technologies</p>
            <h3>Quick Summary/Importance of Project</h3>
            <p>INSERT DETAILS HERE</p>
            <p>INSERT DETAILS HERE</p>
            <p>INSERT DETAILS HERE</p>
            <p>INSERT DETAILS HERE</p>

        </div>

        <div class="project-list-container">
            <div class="project-card">1</div>
            <div class="project-card">2</div>
            <div class="project-card">3</div>
            <div class="project-card">4</div>
            <div class="project-card">5</div>
        </div>
    </div>
</template>

<style scoped>
    .projects-section {
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: lightpink;
    }

    .project-info-container {
        width: 65%;
        padding: 1rem;
        margin: 1rem;
        border-style: solid;
    }

    .project-title {
        margin: 0 auto;
    }

    .project-list-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 35%;
        padding: 1rem;
        margin: 1rem;
        border-style: solid;
    }

    .project-card {
        padding: 0.5rem;
        margin: 0.5rem;
        border-style: solid;
        border-radius: 20px;
        width: 40%;

        transition: 
            width 0.2s ease,
            padding 0.2s ease,
            border-color 0.2s ease
    }

    .project-card:hover {
        border-color: blue;
        width: 65%;
        padding: 1rem;
        cursor: pointer;
    }

</style>
