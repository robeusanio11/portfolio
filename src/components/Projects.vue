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
                <h4 class="project-summary">{{displayProject.summary}}</h4>
                <span>Technologies: </span>
                <span v-for="tech in displayProject.technologies">{{tech}}, </span>
                <!-- <p>{{displayProject.description}}</p> -->
                <ul>
                    <li v-for="bullet in displayProject.bullets">{{bullet}}</li>
                </ul>
                <img class="project-image" :src="displayProject.image" alt="project media"/>
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
                <!-- <p>{{project.title}}</p> -->
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
        /* display: flex;
        flex-direction: column;
        align-items: center; */
        width: 65%;
        padding: 1rem;
        margin: 1rem;
        border-radius: 20px;
        background-color: rgba(255, 255, 255, .075);
        /* border-style: solid; */
    }
    .project-info-container > h3 {
        /* color: #6c2dffff; */
        color: rgb(200, 200, 200);
        font-weight: 400;
        margin: 0 0 0.5rem 0;
    }
    
    .project-info-container > span {
        color: rgb(150, 150, 150);
        margin: 0.5rem 0 0.5rem 0;
    }

    .project-heading {
        display: flex;
        flex-direction: row;
        align-items: baseline;
        margin: 0;
        margin-bottom: 1rem;
    }

    .project-heading > h1 {
        margin: 1rem 1rem 0 0;
        color: #6c2dffff;
        font-weight: 400;
    }

    .project-heading > h3, h4 {
        font-weight: 400;
        margin: 0 0 0.5rem 0;
    }

    .project-summary {
        color: #6c2dffff;
        font-weight: 500;
        margin: 0 0 0.5rem 0;
    }

    .project-image {
        display: block;
        margin: 2rem auto;
        width: 50%;
        border-radius: 20px;
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
        /* border: 2px solid gray; */
        /* border-style: solid; */
        border-radius: 20px;
        width: 55%;
        /* background-color: rgba(255, 255, 255, .075); */
    }

    .project-card:hover {
        /* border-color: #470099ff; */
        width: 65%;
        padding: 1rem;
        cursor: pointer;
        transition: all 0.2s ease;
        color: #6c2dffff;
        text-shadow: 
            0 0 5px rgb(50,50,50),
            0 0 10px rgb(50,50,50)
    }
    .project-card.active {
        width: 65%;
        padding: 1rem;
        color: white;
        font-weight: 100;
        text-shadow: 
            0 0 5px #6c2dffff,
            0 0 10px #6c2dffff
        /* border-color: #470099ff; */
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

    /* Tablet */
    @media (max-width: 1024px) {
        .project-info-container {
            width: 60%;
            padding: 0.75rem;
            margin: 0.5rem;
        }

        .project-list-container {
            width: 40%;
        }

        .project-image {
            width: 70%;
        }
    }

    /* Mobile */
    @media (max-width: 768px) {
        .projects-section {
            flex-direction: column-reverse;
            overflow-y: auto;
        }

        .project-info-container {
            width: 100%;
            margin: 0.5rem;
            padding: 0.75rem;
            box-sizing: border-box;
        }

        .project-heading {
            flex-direction: column;
            align-items: flex-start;
        }

        .project-heading > h1 {
            font-size: 1.3rem;
            margin: 0.5rem 0 0.25rem 0;
        }

        .project-heading > h3 {
            font-size: 0.9rem;
        }

        .project-image {
            width: 90%;
            margin: 1rem auto;
        }

        .project-list-container {
            width: 100%;
            flex: 0 0 auto;
            padding: 0.5rem;
            margin: 0;
        }

        .project-list-container > h3 {
            margin: 0.5rem 0;
        }

        .project-card {
            width: 80%;
            padding: 0.4rem 0.75rem;
            margin: 0.25rem;
        }

        .project-card:hover,
        .project-card.active {
            width: 85%;
            padding: 0.5rem 1rem;
        }
    }

</style>
