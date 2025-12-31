<script setup>
  import Navbar from './Navbar.vue'
  import About from './About.vue'
  import Projects from './Projects.vue'
  import Contact from './Contact.vue'

</script>

<template>
  <header>
    <Navbar className="navbar"/>
  </header>
  <main>
    <About id="about" />
    <Projects id="projects" />
    <Contact id="contact" />
  </main>
</template>

<style scoped>
div {
  min-height: 100vh;
}
body {
  margin: 0 auto;
}
</style>
