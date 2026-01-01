<script setup>

</script>

<template>
    <div class="about-container">
        <h4>At a Glance</h4>
        <ul class="at-a-glance">
            <li>Full-Stack Software Engineer</li>
            <li>California, USA (Open to Relocation)</li>
            <li>Email: robeusanio11@gmail.com</li>
            <li>Phone: (209) 814-7968</li>
        </ul>
        <h4>Deep Dive</h4>
        <p>I am a Full Stack Software Engineer with a strong passion for problem solving and community building! As an engineer, I strive to demonstrate these passions within the community of my team to ensure a healthy and productive workplace. I am very eager to leave a lasting impact on people's day to day lives by creating positive and impactful experiences on the users of projects I work on.</p>
        <a class="resume-button" href="src/assets/Rob_Eusanio_Resume.pdf" download="Rob-Eusanio-Resume">Download Resume</a>
    </div>

</template>

<style scoped>
    
    .about-container > p {
        text-indent: 2rem;
    }

    h4 {
        margin: 1rem 0rem 1rem 0rem;
    }

    .at-a-glance {
        margin-bottom: 2rem;
    }

    .resume-button {
        display: inline-block;
        background-color: rgba(255, 255, 255, .075);
        color: rgb(200, 200, 200);;
        border: 2px solid gray;
        border-radius: 20px;
        padding: 0.5rem;
        text-decoration: none;
        transition: 
            border-color 0.2s ease,
            transform 0.2s ease;
    }

    .resume-button:hover {
        border: 2px solid #470099ff;
        cursor: pointer;
    }

    .resume-button:active {
        background-color: rgba(255, 255, 255, .1);
        transform: scale(0.97);
    }

</style>
