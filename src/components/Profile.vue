<script setup>
    import {ref} from 'vue';
    import About from './About.vue';
    import Education from './Education.vue';
    import Enrichment from './Enrichment.vue';

    var display = ref("about");
</script>

<template>
    <div class="profile-container">
        <div class="profile-cards">
            <h2>Rob Eusanio</h2>
            <img class="image-card" src="/profile-photo.JPG" alt="Robert Eusanio Headshot" />
            <div class="card">
                <h5>Title</h5>
                <p>Full-Stack Software Engineer</p>
            </div>
            <div class="card">
                <h5>Location</h5>
                <p>California, USA (Open to Relocation)</p>
            </div>
            <div class="card">
                <h5>Contact Info</h5>
                <p>Email: robeusanio11@gmail.com</p>
                <p>Phone: (209) 814-7968</p>
            </div>
            <div class="button-links">
                <a class="linkedin-button" href="https://www.linkedin.com/in/robeusanio/">
                    <img src="/lnBug-White.png" title="LinkedIn" alt="LinkedIn Icon" />
                </a>
                <a class="github-button" href="https://github.com/robeusanio11">
                    <img src="/github-mark-white.png" title="Github" alt="Github Icon" />
                </a>
                <a class="resume-button" href="/Rob_Eusanio_Resume.pdf">
                    <img src="/icons8-resume-100-white.png" title="Resume" alt="Resume Icon" />
                </a>
            </div>
        </div>
        <div class="profile-info">
            <h2>MY PROFILE</h2>
            <a 
                v-for="section in ['about', 'education', 'enrichment']"
                :id="section"
                :class="{ active: display === section}"
                @click="display = section"
            >{{section.toUpperCase()}}</a>
            <hr class="line-break"/>
            <Transition mode="out-in">
                <div v-if="display === 'about'">
                    <About/>
                </div>
                <div v-else-if="display === 'education'">
                    <Education/>
                </div>
                <div v-else-if="display === 'enrichment'">
                    <Enrichment/>
                </div>
            </Transition>
        </div>
    </div>
</template>

<style scoped>
    .profile-container {
        display: flex;
        flex-direction: row;
        align-items: start;
        width: 100%;
    }

    .profile-cards {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 30%;
        padding: 1rem;
    }

    .card {
        padding: 0.5rem;
        margin: 0.5rem;
        width: 60%;
        border-radius: 20px;
        border: 2px solid gray;
        background-color: rgba(255, 255, 255, .075);
        transition: all 0.3s ease;
    }

    .card:hover {
        border-color: #9263ffff;
        padding: .75rem;
        box-shadow:
            0 0 10px rgba(108, 45, 255, 0.3),
            0 0 20px rgba(108, 45, 255, 0.2);
    }

    .card > * {
        margin: 0 auto;
    }

    .image-card {
        width: 25rem;
        height: 25rem;
        margin: 1rem;
        border: 2px solid white;
        border-radius: 20px;
        transition: all 0.3s ease;
    }

    .image-card:hover {
        border-color: #9263ffff;
        box-shadow:
            0 0 15px rgba(108, 45, 255, 0.4),
            0 0 30px rgba(108, 45, 255, 0.3);
    }

    .button-links {
        display: flex;
        gap: 1rem;
    }

    .button-links a {
        transition: all 0.3s ease;
    }

    .button-links a:hover {
        filter: drop-shadow(0 0 8px #9263ffff) drop-shadow(0 0 15px #6c2dffff);
    }

    img {
        width: 2rem;
        height: 2rem;
        margin: 2rem 2rem 0 2rem;
    }

    .profile-info {
        background-color: rgba(255, 255, 255, .075);
        border-radius: 20px;
        flex-grow: 1;
        margin: 5rem 5rem 5rem 5rem;
        padding: 1.5rem 2rem;
        width: 80%;
    }
    
    .profile-info > a {
        margin-right: 1rem;
        color: rgb(225,225,225);
        cursor: pointer;
        transition: all 0.3s ease;
    }

    .profile-info > a:hover {
        color: #9263ffff;
        text-shadow:
            0 0 10px #6c2dffff,
            0 0 20px #6c2dffff,
            0 0 30px #6c2dffff;
    }

    a.active {
        color: #9263ffff;
        font-weight: 400;
        text-shadow:
            0 0 10px #6c2dffff,
            0 0 20px #6c2dffff,
            0 0 30px #6c2dffff;
    }

    .line-break {
        display: block;
        height: 1px;
        width: 100%;
        border: 0;
        border-top: 1px solid rgba(255, 255, 255, 0.2);
        margin-top: 1em;
        padding: 0;
    }

    .v-enter-active,
    .v-leave-active {
        transition: all 0.2s ease;
    }

    .v-enter-from {
        transform: translateX(20px);
        opacity: 0;
    }

    .v-leave-to {
        transform: translateX(-20px);
        opacity: 0;
    }

</style>