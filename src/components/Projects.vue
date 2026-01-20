<script setup>
    import {ref} from 'vue';

    import projects from '../assets/projects.json'

    var displayProject = ref(projects[0]);

</script>

<template>
    <div class="projects-section">
        <!-- Tabs at top -->
        <div class="project-tabs">
            <div
                class="project-tab"
                v-for="(project, index) in projects"
                :key="index"
                @click="displayProject = projects[index]"
                :class="{active: project.name === displayProject.name }">
                {{project.name}}
            </div>
        </div>

        <!-- Content area -->
        <Transition name="project-info" mode="out-in">
            <div class="project-content" :key="displayProject.name">
                <!-- Left: Details -->
                <div class="project-details">
                    <div class="project-header">
                        <h1 class="project-name">{{displayProject.name}}</h1>
                        <span class="project-company">{{displayProject.company}}</span>
                    </div>
                    <p class="project-title">{{displayProject.title}}</p>

                    <div class="project-divider"></div>

                    <p class="project-summary">{{displayProject.summary}}</p>

                    <div class="project-technologies">
                        <span
                            class="tech-badge"
                            v-for="(tech, index) in displayProject.technologies"
                            :key="index">
                            {{tech}}
                        </span>
                    </div>

                    <h4 class="highlights-label">Highlights</h4>
                    <ul class="project-bullets">
                        <li v-for="(bullet, index) in displayProject.bullets" :key="index">
                            <span class="bullet-text">{{bullet}}</span>
                        </li>
                    </ul>
                </div>

                <!-- Right: Preview -->
                <div class="project-preview">
                    <div class="image-container">
                        <img class="project-image" :src="displayProject.image" alt="project media"/>
                    </div>
                    <div class="project-links">
                        <a
                            class="project-link"
                            :href="displayProject.github || '#'"
                            target="_blank"
                            :class="{disabled: !displayProject.github}">
                            <span class="link-icon">&#60;/&#62;</span>
                            GitHub
                        </a>
                        <a
                            class="project-link project-link-primary"
                            :href="displayProject.demo || '#'"
                            target="_blank"
                            :class="{disabled: !displayProject.demo}">
                            <span class="link-icon">&#9654;</span>
                            Live Demo
                        </a>
                    </div>
                </div>
            </div>
        </Transition>
    </div>
</template>

<style scoped>
    .projects-section {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 1rem;
        height: calc(100vh - var(--navbar-height));
        overflow: hidden;
        box-sizing: border-box;
    }

    /* Tabs */
    .project-tabs {
        display: flex;
        justify-content: center;
        gap: 1rem;
        padding: 1rem;
        width: 100%;
        flex-shrink: 0;
    }

    .project-tab {
        padding: 0.5rem 1.5rem;
        border-radius: 20px;
        background-color: rgba(255, 255, 255, .075);
        border: 2px solid gray;
        cursor: pointer;
        transition: all 0.3s ease;
        font-size: 0.9rem;
    }

    .project-tab:hover {
        border-color: #9263ffff;
        color: #9263ffff;
        box-shadow:
            0 0 10px rgba(108, 45, 255, 0.2),
            0 0 20px rgba(108, 45, 255, 0.1);
    }

    .project-tab.active {
        background-color: #9263ffff;
        border-color: #9263ffff;
        color: white;
        box-shadow:
            0 0 10px rgba(108, 45, 255, 0.3),
            0 0 20px rgba(108, 45, 255, 0.2);
    }

    /* Content area */
    .project-content {
        display: flex;
        flex-direction: row;
        width: 100%;
        padding: 1.5rem;
        margin-top: 1rem;
        border-radius: 20px;
        background-color: rgba(255, 255, 255, .075);
        border: 1px solid rgba(255, 255, 255, 0.1);
        flex: 1;
        min-height: 0;
        overflow-y: auto;
        overflow-x: hidden;
        box-sizing: border-box;
    }

    .project-content::-webkit-scrollbar {
        width: 8px;
    }

    .project-content::-webkit-scrollbar-track {
        background: rgba(255, 255, 255, 0.1);
        border-radius: 20px;
        margin: 20px 0;
    }

    .project-content::-webkit-scrollbar-thumb {
        background: rgba(146, 99, 255, 0.5);
        border-radius: 20px;
    }

    .project-content::-webkit-scrollbar-thumb:hover {
        background: rgba(146, 99, 255, 0.7);
    }

    /* Left: Details */
    .project-details {
        width: 60%;
        padding: 1rem 2rem 1rem 1rem;
    }

    .project-header {
        margin-bottom: 0.5rem;
    }

    .project-name {
        margin: 0;
        font-family: 'Segoe UI', 'Helvetica Neue', Arial, sans-serif;
        font-size: 2.25rem;
        font-weight: 300;
        letter-spacing: 0.02rem;
        color: #9263ffff;
        text-shadow: 0 0 8px rgba(255, 255, 255, 0.3);
    }

    .project-company {
        font-size: 1rem;
        color: rgb(180, 180, 180);
        font-style: italic;
    }

    .project-title {
        color: rgb(200, 200, 200);
        font-size: 1.1rem;
        font-weight: 300;
        margin: 0.5rem 0 1rem 0;
    }

    .project-divider {
        height: 1px;
        background: linear-gradient(90deg, #6c2dffff, transparent);
        margin: 1rem 0;
        width: 80%;
    }

    .project-summary {
        color: rgb(220, 220, 220);
        font-size: 1.05rem;
        line-height: 1.6;
        margin: 0 0 1.5rem 0;
    }

    .project-technologies {
        display: flex;
        flex-wrap: wrap;
        gap: 0.5rem;
        margin-bottom: 1.5rem;
    }

    .tech-badge {
        padding: 0.3rem 0.75rem;
        border-radius: 15px;
        background-color: rgba(108, 45, 255, 0.15);
        border: 1px solid rgba(108, 45, 255, 0.3);
        color: #b8a0ff;
        font-size: 0.8rem;
        transition: all 0.3s ease;
    }

    .tech-badge:hover {
        background-color: rgba(108, 45, 255, 0.25);
        border-color: #9263ffff;
        box-shadow: 0 0 10px rgba(108, 45, 255, 0.2);
    }

    .highlights-label {
        color: #9263ffff;
        font-size: 1rem;
        font-weight: 500;
        margin: 0 0 0.75rem 0;
        text-transform: uppercase;
        letter-spacing: 0.05rem;
    }

    .project-bullets {
        margin: 0;
        padding-left: 0;
        list-style: none;
    }

    .project-bullets > li {
        position: relative;
        padding-left: 1.5rem;
        margin-bottom: 0.75rem;
        line-height: 1.6;
    }

    .project-bullets > li::before {
        content: '▹';
        position: absolute;
        left: 0;
        color: #9263ffff;
        font-size: 1rem;
    }

    .bullet-text {
        color: rgb(200, 200, 200);
    }

    /* Right: Preview */
    .project-preview {
        width: 40%;
        padding: 1rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
    }

    .image-container {
        width: 100%;
        max-width: 400px;
        border-radius: 20px;
        overflow: hidden;
        border: 2px solid rgba(255, 255, 255, 0.1);
        transition: all 0.3s ease;
    }

    .image-container:hover {
        border-color: #9263ffff;
        box-shadow:
            0 0 20px rgba(108, 45, 255, 0.3),
            0 0 40px rgba(108, 45, 255, 0.15);
    }

    .project-image {
        width: 100%;
        display: block;
        transition: transform 0.3s ease;
    }

    .image-container:hover .project-image {
        transform: scale(1.02);
    }

    .project-links {
        display: flex;
        gap: 1rem;
        margin-top: 1.5rem;
    }

    .project-link {
        display: flex;
        align-items: center;
        gap: 0.5rem;
        padding: 0.6rem 1.25rem;
        border-radius: 20px;
        background-color: rgba(255, 255, 255, .075);
        border: 2px solid gray;
        color: rgb(200, 200, 200);
        text-decoration: none;
        transition: all 0.3s ease;
        font-size: 0.9rem;
    }

    .link-icon {
        font-size: 0.85rem;
    }

    .project-link:hover {
        border-color: #9263ffff;
        color: #9263ffff;
        box-shadow:
            0 0 10px rgba(108, 45, 255, 0.3),
            0 0 20px rgba(108, 45, 255, 0.2);
    }

    .project-link-primary {
        background-color: #9263ffff;
        border-color: #9263ffff;
        color: white;
    }

    .project-link-primary:hover {
        background-color: #7c4dff;
        color: white;
        box-shadow:
            0 0 15px rgba(108, 45, 255, 0.5),
            0 0 30px rgba(108, 45, 255, 0.3);
    }

    .project-link.disabled {
        opacity: 0.4;
        cursor: not-allowed;
        pointer-events: none;
    }

    /* Transitions */
    .project-info-enter-active,
    .project-info-leave-active {
        transition: all 0.2s ease;
    }

    .project-info-enter-from {
        opacity: 0;
        transform: translateY(1rem);
    }

    .project-info-leave-to {
        opacity: 0;
        transform: translateY(-1rem);
    }

    /* Tablet */
    @media (max-width: 1024px) {
        .project-tabs {
            flex-wrap: wrap;
            gap: 0.75rem;
            padding: 0.75rem;
        }

        .project-tab {
            padding: 0.4rem 1rem;
            font-size: 0.85rem;
        }

        .project-content {
            padding: 1rem;
        }

        .project-details {
            width: 55%;
            padding: 0.75rem 1rem 0.75rem 0.5rem;
        }

        .project-name {
            font-size: 1.75rem;
        }

        .project-company {
            font-size: 0.9rem;
        }

        .project-title {
            font-size: 1rem;
        }

        .project-summary {
            font-size: 0.95rem;
        }

        .tech-badge {
            padding: 0.25rem 0.6rem;
            font-size: 0.75rem;
        }

        .project-preview {
            width: 45%;
            padding: 0.75rem;
        }

        .image-container {
            max-width: 300px;
        }

        .project-link {
            padding: 0.5rem 1rem;
            font-size: 0.85rem;
        }
    }

    /* Mobile */
    @media (max-width: 768px) {
        .projects-section {
            padding: 0.5rem;
            height: calc(100vh - var(--navbar-height));
        }

        .project-tabs {
            flex-wrap: wrap;
            gap: 0.5rem;
            padding: 0.5rem;
        }

        .project-tab {
            padding: 0.35rem 0.75rem;
            font-size: 0.75rem;
        }

        .project-content {
            flex-direction: column;
            padding: 1rem;
            margin-top: 0.5rem;
        }

        .project-details {
            width: 100%;
            padding: 0.5rem;
            order: 2;
        }

        .project-header {
            text-align: center;
        }

        .project-name {
            font-size: 1.5rem;
        }

        .project-company {
            font-size: 0.85rem;
            display: block;
            margin-top: 0.25rem;
        }

        .project-title {
            font-size: 0.9rem;
            text-align: center;
        }

        .project-divider {
            width: 60%;
            margin: 0.75rem auto;
        }

        .project-summary {
            font-size: 0.9rem;
            text-align: center;
            margin-bottom: 1rem;
        }

        .project-technologies {
            justify-content: center;
            gap: 0.4rem;
            margin-bottom: 1rem;
        }

        .tech-badge {
            padding: 0.2rem 0.5rem;
            font-size: 0.7rem;
        }

        .highlights-label {
            font-size: 0.9rem;
            text-align: center;
        }

        .project-bullets {
            padding-left: 0.5rem;
        }

        .project-bullets > li {
            padding-left: 1.25rem;
            margin-bottom: 0.5rem;
            font-size: 0.85rem;
            line-height: 1.5;
        }

        .project-preview {
            width: 100%;
            padding: 0.5rem;
            order: 1;
            margin-bottom: 1rem;
        }

        .image-container {
            max-width: 100%;
        }

        .project-links {
            margin-top: 1rem;
            gap: 0.75rem;
        }

        .project-link {
            padding: 0.5rem 1rem;
            font-size: 0.8rem;
            gap: 0.4rem;
        }

        .link-icon {
            font-size: 0.75rem;
        }
    }

</style>
