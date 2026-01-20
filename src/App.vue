<script setup>
  import Profile from './components/Profile.vue'
  import Projects from './components/Projects.vue'
  import Contact from './components/Contact.vue'
  import SectionNav from './components/SectionNav.vue'
</script>

<template>
  <main>
    <section id="profile" class="section">
      <div class="section-content">
        <Profile />
      </div>
      <SectionNav :currentIndex="0" />
    </section>
    <section id="projects" class="section">
      <div class="section-content">
        <Projects />
      </div>
      <SectionNav :currentIndex="1" />
    </section>
    <section id="contact" class="section">
      <div class="section-content">
        <Contact />
      </div>
      <SectionNav :currentIndex="2" />
    </section>
  </main>
</template>

<style scoped>
  main {
    background: radial-gradient(closest-side, #000000ff 0%, #0e0e47e3 200%);
  }

  .section {
    height: 100vh;
    padding: 2rem 1rem;
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
  }

  .section-content {
    flex: 1;
    display: flex;
    flex-direction: column;
    overflow: hidden;
    min-height: 0;
  }

  .section-content > * {
    flex: 1;
    overflow-x: hidden;
    overflow-y: auto;
    min-height: 0;
  }

  /* Tablet */
  @media (max-width: 1024px) {
    .section {
      padding: 1.5rem 0.75rem;
    }
  }

  /* Mobile */
  @media (max-width: 768px) {
    .section {
      padding: 1rem 0.5rem;
    }
  }
</style>
