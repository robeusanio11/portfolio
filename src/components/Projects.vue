<script setup>
    import { ref } from 'vue'
    import projects from '../assets/projects.json'

    const selectedProject = ref(null)

    function openProject(project) {
        selectedProject.value = project
    }

    function closeProject() {
        selectedProject.value = null
    }
</script>

<template>
    <div class="projects-section">
        <h2 class="section-title">My Projects</h2>

        <!-- Horizontal scrollable cards -->
        <div class="projects-scroll-container">
            <div class="projects-row">
                <div
                    class="project-card"
                    v-for="(project, index) in projects"
                    :key="index"
                    @click="openProject(project)">
                    <!-- Image -->
                    <div class="card-image-container">
                        <img class="card-image" :src="project.image" alt="project preview"/>
                        <div class="card-image-overlay"></div>
                    </div>

                    <!-- Content -->
                    <div class="card-content">
                        <h3 class="card-title">{{ project.name }}</h3>
                        <span class="card-role">{{ project.title }}</span>

                        <div class="card-technologies">
                            <span
                                class="tech-badge"
                                v-for="(tech, techIndex) in project.technologies.slice(0, 3)"
                                :key="techIndex">
                                {{ tech }}
                            </span>
                            <span class="tech-badge tech-more" v-if="project.technologies.length > 3">
                                +{{ project.technologies.length - 3 }}
                            </span>
                        </div>

                        <span class="card-hint">Click to view details</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Expanded detail overlay -->
        <Transition name="overlay">
            <div class="project-overlay" v-if="selectedProject" @click.self="closeProject">
                <Transition name="modal">
                    <div class="project-modal" v-if="selectedProject">
                        <button class="modal-close" @click="closeProject">&times;</button>

                        <div class="modal-content">
                            <!-- Left: Image + Links -->
                            <div class="modal-left">
                                <div class="modal-image-container">
                                    <img class="modal-image" :src="selectedProject.image" alt="project preview"/>
                                </div>

                                <div class="modal-links">
                                    <a
                                        class="modal-link"
                                        :href="selectedProject.github || '#'"
                                        target="_blank"
                                        :class="{ disabled: !selectedProject.github }"
                                        @click.stop>
                                        <span class="link-icon">&#60;/&#62;</span>
                                        GitHub
                                    </a>
                                    <a
                                        class="modal-link modal-link-primary"
                                        :href="selectedProject.demo || '#'"
                                        target="_blank"
                                        :class="{ disabled: !selectedProject.demo }"
                                        @click.stop>
                                        <span class="link-icon">&#9654;</span>
                                        Live Demo
                                    </a>
                                </div>
                            </div>

                            <!-- Right: Details -->
                            <div class="modal-details">
                                <div class="modal-header">
                                    <h2 class="modal-title">{{ selectedProject.name }}</h2>
                                    <span class="modal-company">{{ selectedProject.company }}</span>
                                    <p class="modal-role">{{ selectedProject.title }}</p>
                                </div>

                                <p class="modal-summary">{{ selectedProject.summary }}</p>

                                <div class="modal-technologies">
                                    <span
                                        class="tech-badge"
                                        v-for="(tech, techIndex) in selectedProject.technologies"
                                        :key="techIndex">
                                        {{ tech }}
                                    </span>
                                </div>

                                <h4 class="highlights-label">Highlights</h4>
                                <ul class="modal-bullets">
                                    <li v-for="(bullet, bulletIndex) in selectedProject.bullets" :key="bulletIndex">
                                        {{ bullet }}
                                    </li>
                                </ul>

                            </div>
                        </div>
                    </div>
                </Transition>
            </div>
        </Transition>
    </div>
</template>

<style scoped>
    .projects-section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 2rem;
        min-height: calc(100vh - var(--navbar-height));
        box-sizing: border-box;
    }

    .section-title {
        text-align: center;
        font-size: 2rem;
        font-weight: 300;
        color: #9263ffff;
        margin: 0 0 1rem 0;
        letter-spacing: 0.05rem;
        text-shadow: 0 0 20px rgba(146, 99, 255, 0.3);
    }

    /* Horizontal scroll container */
    .projects-scroll-container {
        width: 100%;
        overflow-x: auto;
        overflow-y: hidden;
        padding: 1rem 0 2rem 0;
        scrollbar-width: thin;
        scrollbar-color: rgba(146, 99, 255, 0.5) rgba(255, 255, 255, 0.1);
    }

    .projects-scroll-container::-webkit-scrollbar {
        height: 8px;
    }

    .projects-scroll-container::-webkit-scrollbar-track {
        background: rgba(255, 255, 255, 0.1);
        border-radius: 10px;
    }

    .projects-scroll-container::-webkit-scrollbar-thumb {
        background: rgba(146, 99, 255, 0.5);
        border-radius: 10px;
    }

    .projects-scroll-container::-webkit-scrollbar-thumb:hover {
        background: rgba(146, 99, 255, 0.7);
    }

    .projects-row {
        display: flex;
        gap: 1.25rem;
        padding: 0.5rem;
        width: max-content;
        margin: 0 auto;
    }

    /* Cards */
    .project-card {
        width: 280px;
        flex-shrink: 0;
        background: rgba(255, 255, 255, 0.05);
        border: 1px solid rgba(255, 255, 255, 0.1);
        border-radius: 16px;
        overflow: hidden;
        cursor: pointer;
        transition: all 0.3s ease;
    }

    .project-card:hover {
        transform: translateY(-6px);
        border-color: #9263ffff;
        box-shadow:
            0 15px 30px rgba(0, 0, 0, 0.3),
            0 0 25px rgba(146, 99, 255, 0.2),
            0 0 50px rgba(146, 99, 255, 0.1);
    }

    .card-image-container {
        position: relative;
        width: 100%;
        aspect-ratio: 16 / 10;
        overflow: hidden;
        background: rgba(0, 0, 0, 0.3);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .card-image {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.3s ease;
    }

    .project-card:hover .card-image {
        transform: scale(1.05);
    }

    .card-image-overlay {
        position: absolute;
        inset: 0;
        background: linear-gradient(
            to bottom,
            transparent 0%,
            transparent 40%,
            rgba(0, 0, 0, 0.7) 100%
        );
        pointer-events: none;
    }

    .card-content {
        padding: 1.25rem;
    }

    .card-title {
        margin: 0;
        font-size: 1.1rem;
        font-weight: 500;
        color: #9263ffff;
    }

    .card-role {
        font-size: 0.8rem;
        color: rgb(160, 160, 160);
        display: block;
        margin-bottom: 0.75rem;
    }

    .card-technologies {
        display: flex;
        flex-wrap: wrap;
        gap: 0.35rem;
        margin-bottom: 0.75rem;
    }

    .tech-badge {
        padding: 0.2rem 0.5rem;
        border-radius: 10px;
        background-color: rgba(108, 45, 255, 0.15);
        border: 1px solid rgba(108, 45, 255, 0.3);
        color: #b8a0ff;
        font-size: 0.65rem;
        transition: all 0.3s ease;
    }

    .tech-more {
        background-color: rgba(255, 255, 255, 0.1);
        border-color: rgba(255, 255, 255, 0.2);
        color: rgb(180, 180, 180);
    }

    .card-hint {
        font-size: 0.7rem;
        color: rgb(120, 120, 120);
        font-style: italic;
    }

    /* Overlay */
    .project-overlay {
        position: fixed;
        inset: 0;
        background: rgba(0, 0, 0, 0.85);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1000;
        padding: 2rem;
        backdrop-filter: blur(4px);
    }

    /* Modal */
    .project-modal {
        position: relative;
        background: linear-gradient(145deg, rgba(30, 30, 40, 0.98), rgba(20, 20, 28, 0.98));
        border: 1px solid rgba(146, 99, 255, 0.3);
        border-radius: 20px;
        max-width: 1000px;
        max-height: 90vh;
        overflow-y: auto;
        box-shadow:
            0 25px 60px rgba(0, 0, 0, 0.5),
            0 0 40px rgba(146, 99, 255, 0.15);
    }

    .modal-close {
        position: absolute;
        top: 1rem;
        right: 1rem;
        background: rgba(255, 255, 255, 0.1);
        border: 1px solid rgba(255, 255, 255, 0.2);
        color: white;
        width: 36px;
        height: 36px;
        border-radius: 50%;
        font-size: 1.5rem;
        cursor: pointer;
        transition: all 0.3s ease;
        display: flex;
        align-items: center;
        justify-content: center;
        line-height: 1;
        z-index: 10;
    }

    .modal-close:hover {
        background: rgba(146, 99, 255, 0.3);
        border-color: #9263ffff;
    }

    .modal-content {
        display: flex;
        gap: 2rem;
        padding: 2rem;
    }

    .modal-left {
        flex-shrink: 0;
        width: 400px;
        display: flex;
        flex-direction: column;
        align-items: center;
        align-self: center;
        gap: 1rem;
    }

    .modal-image-container {
        width: 100%;
        height: fit-content;
        border-radius: 12px;
        overflow: hidden;
        border: 1px solid rgba(255, 255, 255, 0.1);
        background: rgba(0, 0, 0, 0.3);
    }

    .modal-image {
        width: 100%;
        display: block;
    }

    .modal-details {
        flex: 1;
        min-width: 0;
    }

    .modal-header {
        margin-bottom: 1rem;
    }

    .modal-title {
        margin: 0;
        font-size: 1.75rem;
        font-weight: 400;
        color: #9263ffff;
        text-shadow: 0 0 10px rgba(146, 99, 255, 0.3);
    }

    .modal-company {
        font-size: 0.95rem;
        color: rgb(160, 160, 160);
        font-style: italic;
    }

    .modal-role {
        font-size: 1rem;
        color: rgb(200, 200, 200);
        margin: 0.5rem 0 0 0;
    }

    .modal-summary {
        color: rgb(210, 210, 210);
        font-size: 1rem;
        line-height: 1.6;
        margin: 0 0 1.25rem 0;
    }

    .modal-technologies {
        display: flex;
        flex-wrap: wrap;
        gap: 0.4rem;
        margin-bottom: 1.25rem;
    }

    .modal-technologies .tech-badge {
        font-size: 0.75rem;
        padding: 0.25rem 0.6rem;
    }

    .highlights-label {
        color: #9263ffff;
        font-size: 0.9rem;
        font-weight: 500;
        margin: 0 0 0.75rem 0;
        text-transform: uppercase;
        letter-spacing: 0.05rem;
    }

    .modal-bullets {
        margin: 0 0 1.5rem 0;
        padding-left: 0;
        list-style: none;
    }

    .modal-bullets > li {
        position: relative;
        padding-left: 1.25rem;
        margin-bottom: 0.6rem;
        color: rgb(200, 200, 200);
        font-size: 0.9rem;
        line-height: 1.5;
    }

    .modal-bullets > li::before {
        content: '▹';
        position: absolute;
        left: 0;
        color: #9263ffff;
    }

    .modal-links {
        display: flex;
        gap: 1rem;
    }

    .modal-link {
        display: flex;
        align-items: center;
        gap: 0.5rem;
        padding: 0.6rem 1.25rem;
        border-radius: 20px;
        background-color: rgba(255, 255, 255, 0.075);
        border: 1px solid rgba(255, 255, 255, 0.2);
        color: rgb(200, 200, 200);
        text-decoration: none;
        transition: all 0.3s ease;
        font-size: 0.9rem;
    }

    .link-icon {
        font-size: 0.85rem;
    }

    .modal-link:hover {
        border-color: #9263ffff;
        color: #9263ffff;
        box-shadow: 0 0 15px rgba(108, 45, 255, 0.3);
    }

    .modal-link-primary {
        background-color: #9263ffff;
        border-color: #9263ffff;
        color: white;
    }

    .modal-link-primary:hover {
        background-color: #7c4dff;
        color: white;
        box-shadow: 0 0 20px rgba(108, 45, 255, 0.5);
    }

    .modal-link.disabled {
        opacity: 0.4;
        cursor: not-allowed;
        pointer-events: none;
    }

    /* Transitions */
    .overlay-enter-active,
    .overlay-leave-active {
        transition: opacity 0.3s ease;
    }

    .overlay-enter-from,
    .overlay-leave-to {
        opacity: 0;
    }

    .modal-enter-active,
    .modal-leave-active {
        transition: all 0.3s ease;
    }

    .modal-enter-from,
    .modal-leave-to {
        opacity: 0;
        transform: scale(0.9) translateY(20px);
    }

    /* Tablet */
    @media (max-width: 1024px) {
        .project-card {
            width: 250px;
        }

        .modal-content {
            flex-direction: column;
            padding: 1.5rem;
        }

        .modal-left {
            width: 100%;
            max-width: 400px;
        }

        .modal-title {
            font-size: 1.5rem;
        }
    }

    /* Mobile */
    @media (max-width: 640px) {
        .projects-section {
            padding: 1rem;
        }

        .project-card {
            width: 220px;
        }

        .card-title {
            font-size: 1rem;
        }

        .project-overlay {
            padding: 1rem;
        }

        .project-modal {
            max-height: 85vh;
        }

        .modal-content {
            padding: 1.25rem;
            gap: 1rem;
        }

        .modal-close {
            top: 0.75rem;
            right: 0.75rem;
            width: 32px;
            height: 32px;
            font-size: 1.25rem;
        }

        .modal-title {
            font-size: 1.3rem;
        }

        .modal-company,
        .modal-role {
            font-size: 0.85rem;
        }

        .modal-summary {
            font-size: 0.9rem;
        }

        .modal-bullets > li {
            font-size: 0.85rem;
        }

        .modal-left {
            width: 100%;
        }

        .modal-links {
            width: 100%;
        }
    }
</style>
