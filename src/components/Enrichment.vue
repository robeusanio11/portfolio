<script setup>
    import {ref} from 'vue';

    var highlighted = ref([]);
</script>

<template>
    <div class="enrichment-container">
        <h4>At a Glance</h4>
        <ul class="at-a-glance">
            <li :class="{active: highlighted.includes('cahsi') }">Computing Alliance for Hispanic Serving Institutions (CAHSI)</li>
            <li :class="{active: highlighted.includes('spara') }">CSU STEM Pathways and Research Alliance (CSU-SPaRA)</li>
            <li :class="{active: highlighted.includes('lsamp') }">Louis Stokes Alliance for Minority Participation (LSAMP)</li>
            <li :class="{active: highlighted.includes('gmis') }">Great Minds in STEM Conference (GMiS) - Research Poster Competition Finalist</li>
            <li :class="{active: highlighted.includes('cwu') }">CodeWithUs - Coding Instructor</li>
            <li :class="{active: highlighted.includes('connected') }">Connected Camps - Coding Instructor</li>
        </ul>
        <h4>Deep Dive</h4>
        <p>Outside of my academic coursework, I have also taken steps to prepare for a career in the software engineering industry by working as a coding instructor for local kids and joining STEM groups. As a <span @mouseover="highlighted = ['cwu', 'connected']" @mouseleave="highlighted = []" class="highlighted-phrase">coding instructor</span> for both <span @mouseover="highlighted = ['cwu']" @mouseleave="highlighted = []" class="highlighted-phrase">CodeWithUs</span> and <span @mouseover="highlighted = ['connected']" @mouseleave="highlighted = []" class="highlighted-phrase">Connected Camps</span>, I had the opportunity to develop an introductory curriculum to coding fundaments and break down concepts into digestible, interactive tutorials. These roles required <span @mouseover="highlighted = ['cwu', 'connected']" @mouseleave="highlighted = []" class="highlighted-phrase">leadership</span>/<span @mouseover="highlighted = ['cwu', 'connected']" @mouseleave="highlighted = []" class="highlighted-phrase">conflict resolution</span> to manage a classroom of 3rd-8th graders. </p>
        <p>While at CSU - Stanislaus, was a part of the <span @mouseover="highlighted = ['cahsi']" @mouseleave="highlighted = []" class="highlighted-phrase">Computing Alliance for Hispanic Serving Institutions</span> (CAHSI), <span @mouseover="highlighted = ['spara']" @mouseleave="highlighted = []" class="highlighted-phrase">CSU STEM Pathways and Research Alliance</span> (CSU-SPaRA), and <span @mouseover="highlighted = ['lsamp']" @mouseleave="highlighted = []" class="highlighted-phrase">Louis Stokes Alliance for Minority Participation</span> (LSAMP). These three organizations provided <span @mouseover="highlighted = ['cahsi', 'spara', 'lsamp']" @mouseleave="highlighted = []" class="highlighted-phrase">mentorship</span>, <span @mouseover="highlighted = ['cahsi', 'spara', 'lsamp']" @mouseleave="highlighted = []" class="highlighted-phrase">networking events</span>, and <span @mouseover="highlighted = ['cahsi', 'spara', 'lsamp']" @mouseleave="highlighted = []" class="highlighted-phrase">career preparedness</span> through activities like workshops and guest lectures in order to provide opportunities and connect students from underrepresented backgrounds.</p>
        <p>During my undergraduate research experience with CAHSI, I was able to present my research in the <span @mouseover="highlighted = ['cahsi', 'gmis']" @mouseleave="highlighted = []" class="highlighted-phrase">Research Poster Competition</span> at the <span @mouseover="highlighted = ['gmis']" @mouseleave="highlighted = []" class="highlighted-phrase">Great Minds in STEM</span> (GMiS) Conference. At the conference I also attended several <span @mouseover="highlighted = ['gmis']" @mouseleave="highlighted = []" class="highlighted-phrase">workshops</span> led by senior engineers to learn about relevant technologies/concepts within <span @mouseover="highlighted = ['gmis']" @mouseleave="highlighted = []" class="highlighted-phrase">deep learning</span>, <span @mouseover="highlighted = ['gmis']" @mouseleave="highlighted = []" class="highlighted-phrase">cybersecurity</span>,and <span @mouseover="highlighted = ['gmis']" @mouseleave="highlighted = []" class="highlighted-phrase">supercomputing</span></p>
    </div>

</template>

<style scoped>
    h4 {
        margin: 1rem 0rem 1rem 0rem;
    }

    .at-a-glance {
        margin-bottom: 2rem;
    }

    .highlighted-phrase {
        color: #9263ffff;
        font-weight: 400;
    }

    .highlighted-phrase:hover {
        text-shadow: 
            0 0 5px #6c2dffff,
            0 0 10px #6c2dffff
    }    

    .enrichment-container > p {
        text-indent: 2rem;
    }

    .active {
        text-shadow: 
            0 0 5px rgb(150,150,150),
            0 0 10px rgb(150,150,150)
    }
</style>
