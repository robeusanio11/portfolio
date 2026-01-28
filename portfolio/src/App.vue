<script setup>
  import Profile from './components/Profile.vue'
  import Projects from './components/Projects.vue'
  import Contact from './components/Contact.vue'
  import GlobalNav from './components/GlobalNav.vue'
</script>

<template>
  <main>
    <section id="profile" class="section">
      <div class="section-content">
        <Profile />
      </div>
    </section>
    <section id="projects" class="section">
      <div class="section-content">
        <Projects />
      </div>
    </section>
    <section id="contact" class="section">
      <div class="section-content">
        <Contact />
      </div>
    </section>
    <GlobalNav />
  </main>
</template>

<style scoped>
  main {
    background: radial-gradient(closest-side, #000000ff 0%, #0e0e47e3 200%);
  }

  .section {
    height: 100vh;
    height: 100dvh;
    padding: 2rem 1rem 5rem;
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
  }

  .section-content {
    flex: 1 1 0%;
    display: flex;
    flex-direction: column;
    overflow: hidden;
    min-height: 0;
    /* Safari flex overflow fix */
    -webkit-flex: 1 1 0%;
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
      padding: 1.5rem 0.75rem 4rem;
    }
  }

  /* Mobile */
  @media (max-width: 768px) {
    .section {
      height: 100dvh;
      min-height: 100dvh;
      padding: 1rem 0.5rem 3.5rem;
    }

  }
</style>
