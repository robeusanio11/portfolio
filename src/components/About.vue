<script setup>
const scrollToProjects = () => {
    const section = document.getElementById('projects');
    if (section) {
        section.scrollIntoView({
            behavior: 'smooth',
            block: 'start'
        });
    }
};
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
        <p>I am a <span class="highlighted-phrase">Full Stack Software Engineer</span> based in <span class="highlighted-phrase">California</span> with a strong passion for <span class="highlighted-phrase">problem solving</span> and <span class="highlighted-phrase">community building</span>. As an engineer, I strive to demonstrate these passions within my teams to ensure a <span class="highlighted-phrase">positive workplace</span> and create <span class="highlighted-phrase">impactful experiences</span> on the users of projects I work on.</p>
        <p>After recently graduating from <span class="highlighted-phrase">CSU - Stanislaus</span> with a <span class="highlighted-phrase">B.S. in Computer Science</span> at the end of last year, I am eager to continue learning by transitioning the software engineering industry. Through my coursework I have developed a strong foundation in computer science topics such as <span class="highlighted-phrase">data structures</span>, <span class="highlighted-phrase">algorithms</span>, and <span class="highlighted-phrase">operating systems</span>.</p>
        <p>Alongside my academics, I have strengthened my technical skills in <span class="highlighted-phrase">full-stack Javascript web-development</span> through <span class="highlighted-phrase">project based learning</span> where I gained practical experience <span class="highlighted-phrase">building web-apps</span> with modern best practices and technologies. My <span class="highlighted-phrase">undergraduate research experiences</span> have also improved my ability to <span class="highlighted-phrase">quickly learn</span> new technologies and <span class="highlighted-phrase">meet deliverables</span> under deadlines.</p>

        <div class="button-group">
            <button class="projects-button" @click="scrollToProjects">See My Projects</button>
            <a class="resume-button" href="/Rob_Eusanio_Resume.pdf" download="Rob-Eusanio-Resume">Download Resume</a>
        </div>
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

    .button-group {
        display: flex;
        gap: 1rem;
        margin-top: 1.5rem;
    }

    .projects-button {
        display: inline-block;
        background-color: #9263ffff;
        color: white;
        border: 2px solid #9263ffff;
        border-radius: 20px;
        padding: 0.75rem 1.5rem;
        font-size: 1rem;
        font-weight: 500;
        cursor: pointer;
        transition: all 0.3s ease;
        box-shadow:
            0 0 10px rgba(108, 45, 255, 0.3),
            0 0 20px rgba(108, 45, 255, 0.2);
    }

    .projects-button:hover {
        background-color: #7c4dff;
        box-shadow:
            0 0 15px rgba(108, 45, 255, 0.5),
            0 0 30px rgba(108, 45, 255, 0.4),
            0 0 45px rgba(108, 45, 255, 0.3);
        text-shadow:
            0 0 10px rgba(255, 255, 255, 0.5);
    }

    .projects-button:active {
        transform: scale(0.97);
    }

    .resume-button {
        display: inline-block;
        background-color: rgba(255, 255, 255, .075);
        color: rgb(200, 200, 200);
        border: 2px solid gray;
        border-radius: 20px;
        padding: 0.75rem 1.5rem;
        text-decoration: none;
        transition: all 0.3s ease;
    }

    .resume-button:hover {
        border-color: #9263ffff;
        color: #9263ffff;
        cursor: pointer;
        box-shadow:
            0 0 10px rgba(108, 45, 255, 0.3),
            0 0 20px rgba(108, 45, 255, 0.2);
        text-shadow:
            0 0 10px #6c2dffff,
            0 0 20px #6c2dffff;
    }

    .resume-button:active {
        background-color: rgba(255, 255, 255, .1);
        transform: scale(0.97);
    }

    .highlighted-phrase {
        color: #9263ffff;
        font-weight: 400;
        transition: all 0.3s ease;
    }

    .highlighted-phrase:hover {
        text-shadow:
            0 0 10px #6c2dffff,
            0 0 20px #6c2dffff,
            0 0 30px #6c2dffff;
    }
</style>
