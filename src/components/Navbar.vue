<script setup>
  const scrollToSection = (id) => {
    const section = document.getElementById(id)
    if (section) {
      section.scrollIntoView({
        behavior: 'smooth',
        block: 'start'
      });
    }
  }
</script>

<template>
    <nav class="navbar">
        <p class="navbar-title">Robert Eusanio</p>
        <div class="navbar-links">
            <a @click="scrollToSection('profile')">About Me</a>
            <a @click="scrollToSection('profile')">Education</a>
            <a @click="scrollToSection('profile')">Career Enrichment</a>
            <a @click="scrollToSection('projects')">Projects</a>
            <a @click="scrollToSection('contact')">Contact</a>
        </div>
    </nav>
</template>

<style scoped>
    nav {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        border-bottom: 2px solid black;
        height: 5rem;
        margin: 0 auto;
        background-color: #9263ffff;
        /* color: rgb(200, 200, 200); */
        color: black;
    }

    p {
        padding: 1rem;
    }

    .navbar-links {
        display: flex;
        flex-direction: row;
        align-items: center;
        margin-right: 2.5rem;
    }

    a {
        padding: 0.5rem;
        margin-right: 2.5rem;
        border-style: solid;
    }

    a:hover {
        color: white;
        cursor: pointer;
    }
</style>