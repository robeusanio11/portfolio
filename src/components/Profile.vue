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
            <img class="image-card" src="/LOLstats1.PNG" alt="Robert Eusanio Headshot" />
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
                    <img src="" alt="LinkedIn Icon" />
                </a>
                <a class="github-button" href="https://github.com/robeusanio11">
                    <img src="" alt="Github Icon" />
                </a>
                <a class="resume-button" href="src/assets/Rob_Eusanio_Resume.pdf" download="Rob-Eusanio-Resume">
                    <img src="" alt="Resume Icon" />
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
            <!-- <a id="about" @click="display = 'about'" :class="">About Me</a>
            <a id="education" @click="display = 'education'">Education</a>
            <a id="enrichment" @click="display = 'enrichment'">Career Enrichment</a> -->
            <div v-if="display === 'about'">
                <About/>
            </div>
            <div v-else-if="display === 'education'">
                <Education/>
            </div>
            <div v-else-if="display === 'enrichment'">
                <Enrichment/>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .profile-container {
        display: flex;
        flex-direction: row;
        /* justify-content: center; */
        align-items: center;
        width: 100%;
        /* background-color: lightblue */
    }

    .profile-container > div {
        /* border-style: solid; */
        padding: 1rem;
        margin: 1rem;
    }

    .profile-cards {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 50%;
    }

    .card {
        padding: 0.5rem;
        margin: 0.5rem;
        width: 60%;
        /* /* border-style: solid; */
        border-radius: 20px;
        border: 2px solid gray;
        transition: 
            width 0.2s ease,
            padding 0.2s ease,
            border-color 0.2s ease
    }

    .card:hover {
        border-color: #470099ff;
        /* border-color: #9263ffff; */
        /* width: 65%; */
        padding: .75rem;
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

    .profile-info {
        background-color: rgba(255, 255, 255, .075);
        width: 40%;
    }
    
    .profile-info > a {
        margin-right: 1rem;
    }

    .profile-info > a:hover {
        cursor: pointer;
    }

    .active {
        /* margin: 10rem; */
        color: #9263ffff; 
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

</style>