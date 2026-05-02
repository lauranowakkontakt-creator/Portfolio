<template>
  <NavBar />
  <HeroSection />
  <hr class="divider" />
  <PortfolioSection />
  <AboutSection />
  <ContactSection />
  <FooterBar />
</template>

<script setup>
import NavBar          from './components/NavBar.vue'
import HeroSection     from './components/HeroSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import AboutSection    from './components/AboutSection.vue'
import ContactSection  from './components/ContactSection.vue'
import FooterBar       from './components/FooterBar.vue'
</script>

<style>
hr.divider {
  border: none;
  border-top: 1px solid var(--border);
  margin: 0 4rem;
}

@media (max-width: 1024px) {
  hr.divider { margin: 0 2.5rem; }
}

@media (max-width: 700px) {
  hr.divider { margin: 0 1.5rem; }
}
</style>
