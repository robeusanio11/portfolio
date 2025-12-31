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
      <a @click="scrollToSection('about')">About Me</a>
      <a @click="scrollToSection('projects')">Projects</a>
      <a @click="scrollToSection('contact')">Contact</a>
    </nav>
</template>

<style scoped>
a {
    padding: 10px
}
</style>