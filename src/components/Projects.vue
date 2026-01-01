<script setup>
    import {ref} from 'vue';

    import projects from '../assets/projects.json'

    var displayProject = ref(projects[0]);

</script>

<template>
    <div class="projects-section">
        <Transition name="project-info" mode="out-in">
            <div class="project-info-container" :key="displayProject.name">
                <div class="project-heading">
                    <h1>{{displayProject.name}}</h1>
                    <h3>{{displayProject.company}}</h3>
                </div>
                <h3>{{displayProject.title}}</h3>
                <span>Technologies: </span>
                <span v-for="tech in displayProject.technologies">{{tech}}, </span>
                <h4>{{displayProject.summary}}</h4>
                <p>{{displayProject.description}}</p>
                <ul>
                    <li v-for="bullet in displayProject.bullets">{{bullet}}</li>
                </ul>
            </div>
        </Transition>

        <div class="project-list-container">
            <h3>Projects:</h3>
            <div 
                class="project-card"
                v-for="(project, index) in projects" 
                :key="index" 
                :id="project.name" 
                @click="displayProject = projects[index]"
                :class="{active: project.name === displayProject.name }">
                <h4>{{project.name}}</h4>
                <p>{{project.title}}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .projects-section {
        display: flex;
        justify-content: center;
        align-items: center;
        /* background-color: lightpink; */
    }

    .project-info-container {
        width: 65%;
        padding: 1rem;
        margin: 1rem;
        background-color: rgba(255, 255, 255, .075);
        /* border-style: solid; */
    }

    .project-heading {
        display: flex;
        flex-direction: row;
        align-items: baseline;
        margin: 0;
    }

    .project-heading > h1 {
        margin-right: 1rem;
    }

    .project-list-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 35%;
        padding: 1rem;
        margin: 1rem;
        /* border-style: solid; */
    }

    .project-card {
        padding: 0.5rem;
        margin: 0.5rem;
        border: 2px solid gray;
        /* border-style: solid; */
        border-radius: 20px;
        width: 55%;
        background-color: rgba(255, 255, 255, .075);
    }

    .project-card:hover {
        border-color: #470099ff;
        width: 65%;
        padding: 1rem;
        cursor: pointer;
        transition: all 0.2s ease;
    }
    .project-card.active {
        width: 65%;
        padding: 1rem;
        border-color: #470099ff;
    }
    .project-card > * {
        margin: 0;
    }

    .project-info-enter-active,
    .project-info-leave-active {
        transition: all 0.2s ease;
    }

    .project-info-enter-from {
        opacity: 0;
        transform: translateX(1rem);
    }

    .project-info-leave-to {
        opacity: 0;
        transform: translateX(-1rem);
    }

</style>
