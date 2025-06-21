<script setup lang="ts">
import { onMounted } from 'vue';
import Navbar from './components/Navbar.vue';
import SectionHero from './components/SectionHero.vue';
import SectionAbout from './components/SectionAbout.vue';
// import SectionAchievements from './components/SectionAchievements.vue';
import SectionPortfolio from './components/SectionPortfolio.vue';
import SectionContact from './components/SectionContact.vue';
import FooterSection from './components/FooterSection.vue';

onMounted(() => {
  // Smooth scrolling for anchor links
  document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', (e) => {
      e.preventDefault();
      
      const targetId = anchor.getAttribute('href');
      if (!targetId) return;
      
      const targetElement = document.querySelector(targetId);
      if (!targetElement) return;
      
      window.scrollTo({
        top: (targetElement as HTMLElement).offsetTop,
        behavior: 'smooth'
      });
    });
  });
});
</script>

<template>
  <div class="app-container">
    <Navbar />
    
    <main>
      <SectionHero />
      <SectionAbout />
      <SectionAchievements />
      <SectionPortfolio />
      <SectionContact />
    </main>
    
    <FooterSection />
  </div>
</template>

<style>
.app-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  flex: 1;
}

@media (max-width: 768px) {
  .container {
    padding: 0 1rem;
  }

  h2 {
    font-size: 2rem;
  }
}
</style>