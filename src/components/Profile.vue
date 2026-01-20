<script setup>
    import {ref} from 'vue';
    import About from './About.vue';
    import Education from './Education.vue';
    import Enrichment from './Enrichment.vue';

    var display = ref("about");
</script>

<template>
    <div class="profile-wrapper">
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
    </div>
</template>

<style scoped>
    /* * {
        box-sizing: border-box;
    } */
    .profile-wrapper {
        /* display: flex; */
        width: 100%;
        height: calc(100vh - var(--navbar-height));
        height: calc(100dvh - var(--navbar-height));
        overflow: hidden;
    }

    .profile-container {
        display: flex;
        flex-direction: row;
        padding: 1px 0;
        
        /* align-items: stretch; */
        /* align-items: flex-start; */
        width: 100%;
        height: 100%;
        min-height: 0;
    }

    .profile-cards {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
        gap: 1rem;
        /* height: 100%; */
        width: 30%;
        padding: 0.5rem;
        /* height: 100%; */
        min-height: 0;
        /* max-height: 100%; */
        /* overflow-y: auto; */
        flex: 0 0 30%;
    }

    .profile-cards > h2 {
        margin: 0;
        font-weight: 200;
        font-size: 2rem;
        letter-spacing: 0.15em;
        text-transform: uppercase;
        color: white;
        text-shadow:
            0 0 10px #9263ffff,
            0 0 20px #6c2dffff,
            0 0 40px rgba(108, 45, 255, 0.5);
    }

    .card {
        padding: 0.5rem;
        margin: .5rem;
        width: 80%;
        border-radius: 20px;
        border: 2px solid gray;
        background-color: rgba(255, 255, 255, .075);
        transition: all 0.3s ease;
    }

    .card:hover {
        /* padding: 1rem; */
        border-color: #9263ffff;
        box-shadow:
            0 0 15px rgba(108, 45, 255, 0.4),
            0 0 30px rgba(108, 45, 255, 0.3);
    }

    .card > * {
        margin: 0 auto;
    }

    .image-card {
        width: 100%;
        height: auto;
        max-width: 18rem;
        aspect-ratio: 1 / 1;
        margin: 0.5rem;
        border: 2px solid white;
        border-radius: 20px;
        transition: all 0.3s ease;
        object-fit: cover;
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
        margin: 0.5rem;
    }

    .profile-info {
        background-color: rgba(255, 255, 255, .075);
        border-radius: 20px;
        flex: 1 1 0;
        min-width: 0;
        margin: 1rem 3rem;
        padding: 1rem 2rem;
        min-height: 0;
        overflow-y: auto;
        align-self: flex-start;
        max-height: 100%;
    }

    .profile-info::-webkit-scrollbar {
        display: block;
        width: 8px;
    }

    .profile-info::-webkit-scrollbar-track {
        background: rgba(255, 255, 255, 0.1);
        border-radius: 20px;
        margin-top: 25px;
        margin-bottom: 25px;
    }

    .profile-info::-webkit-scrollbar-thumb {
        background: rgba(146, 99, 255, 0.5);
        border-radius: 20px;
    }

    .profile-info::-webkit-scrollbar-thumb:hover {
        background: rgba(146, 99, 255, 0.7);
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

    .profile-wrapper,
    .profile-container,
    .profile-cards,
    .profile-info {
        box-sizing: border-box;
    }

    /* Tablet */
    @media (max-width: 1024px) {
        .profile-cards {
            width: 35%;
            flex: 0 0 35%;
        }

        .profile-info {
            margin: 1rem;
            padding: 1rem;
        }

        .image-card {
            max-width: 12rem;
        }
    }

    /* Mobile */
    @media (max-width: 768px) {
        .profile-container {
            flex-direction: column;
            overflow-y: auto;
        }

        .profile-cards {
            width: 100%;
            flex: 0 0 auto;
            flex-direction: row;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
            padding: 0.5rem;
            gap: 0.5rem;
        }

        .profile-cards > h2 {
            margin-right: 1rem;
            font-size: 1.4rem;
            letter-spacing: 0.1em;
        }

        .image-card,
        .card {
            display: none;
        }

        .profile-info {
            margin: 0.5rem;
            padding: 0.75rem;
            flex: 1 1 auto;
            align-self: stretch;
        }

        .profile-info > h2 {
            font-size: 1.2rem;
        }

        .profile-info > a {
            font-size: 0.85rem;
            margin-right: 0.5rem;
        }
    }

</style>