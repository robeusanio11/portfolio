<script setup>
  import Navbar from './components/Navbar.vue'
  import Profile from './components/Profile.vue'
  import Projects from './components/Projects.vue'
  import Contact from './components/Contact.vue'

</script>

<template>
  <header>
    <Navbar className="navbar"/>
  </header>
  <main>
    <Profile id="profile" />
    <Projects id="projects" />
    <Contact id="contact" />
  </main>
</template>

<style scoped>
  div {
    min-height: 100vh;
    background: radial-gradient(closest-side, #000000ff 0%, #0e0e47e3 200%);
  }

  header > * {
    /* border-bottom: 1px solid white; */
  }

  main > * {
    /* border-bottom: 1px solid white; */
  }
</style>
