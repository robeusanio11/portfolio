<script setup>
    import {ref} from 'vue';

    var highlighted = ref('');
</script>

<template>
    <div class="education-container">
        <h4>At a Glance</h4>
        <ul class="at-a-glance">
            <li :class="{active: 'bachelors' === highlighted }">B.S. Computer Science, CSU - Stanislaus (2025)</li>
            <li :class="{active: 'associates' === highlighted }">A.S. Computer Science, San Joaquin Delta College (2023)</li>
            <li :class="{active: 'immersive' === highlighted }">Software Engineering Immersive, Hack Reactor (2021)</li>
        </ul>
        <h4>Deep Dive</h4>
        <p>Although I started my higher education as a Business Major, I quickly found a passion in coding and joined a <span @mouseover="highlighted = 'immersive'" @mouseleave="highlighted = ''" class="highlighted-phrase">Software Engineering Immersive</span> experience, <span @mouseover="highlighted = 'immersive'" @mouseleave="highlighted = ''" class="highlighted-phrase">Hack Reactor</span>, and learned <span @mouseover="highlighted = 'immersive'" @mouseleave="highlighted = ''" class="highlighted-phrase">Full-Stack Web Development</span> with React and Express using SQL and noSQL databases such as MySQL and MongoDB. After completing the program, I returned to college to pursue an <span @mouseover="highlighted = 'associates'" @mouseleave="highlighted = ''" class="highlighted-phrase">A.S in Computer Science</span> from <span @mouseover="highlighted = 'associates'" @mouseleave="highlighted = ''" class="highlighted-phrase">San Joaquin Delta College</span> where I learned coding/CS fundamentals. I followed up my Associates Degree with a <span @mouseover="highlighted = 'bachelors'" @mouseleave="highlighted = ''" class="highlighted-phrase">B.S. Computer Science</span> from <span @mouseover="highlighted = 'bachelors'" @mouseleave="highlighted = ''" class="highlighted-phrase">CSU - Stanislaus</span> which I recently received in Fall of 2025. Here I got to dive deeper into advanced Computer Science concepts where I was able to study topics ranging from the <span @mouseover="highlighted = 'bachelors'" @mouseleave="highlighted = ''" class="highlighted-phrase">Theory of Algorithms</span> to <span @mouseover="highlighted = 'bachelors'" @mouseleave="highlighted = ''" class="highlighted-phrase">Android Development</span> to <span @mouseover="highlighted = 'bachelors'" @mouseleave="highlighted = ''" class="highlighted-phrase">Neural Networks.</span></p>
        
    </div>

</template>

<style scoped>
    
    h4 {
        margin: 1rem 0rem 1rem 0rem;
    }

    .at-a-glance {
        margin-bottom: 2rem;
    }

    .education-container >  p {
        text-indent: 2rem;
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

    .active {
        text-shadow: 
            0 0 5px rgb(150,150,150),
            0 0 10px rgb(150,150,150)
    }

</style>
