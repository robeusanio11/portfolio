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
            <a @click="scrollToSection('about')">About Me</a>
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
        border-style: solid;
        height: 5rem;
        margin: 0 auto;
        background-color: lightgray;
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
        margin: 2.5rem;
        border-style: solid;
    }
    a:hover {
        color: blue;
        cursor: pointer;
    }
</style>