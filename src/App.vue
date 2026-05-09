<template>
  <NavBar />
  <HeroSection />
  <hr class="divider" />
  <PortfolioSection />
  <AboutSection />
  <hr class="divider" />
  <ServicesSection />
  <ContactSection />
  <FooterBar />
</template>

<script setup>
import { onMounted } from 'vue'
import NavBar           from './components/NavBar.vue'
import HeroSection      from './components/HeroSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import AboutSection     from './components/AboutSection.vue'
import ServicesSection  from './components/ServicesSection.vue'
import ContactSection   from './components/ContactSection.vue'
import FooterBar        from './components/FooterBar.vue'

onMounted(() => {
  const revealEls = document.querySelectorAll('.reveal')
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.12, rootMargin: '0px 0px -40px 0px' }
  )
  revealEls.forEach((el) => observer.observe(el))

  document.querySelectorAll('.hero .reveal').forEach((el, i) => {
    setTimeout(() => el.classList.add('visible'), 180 + i * 110)
  })
})
</script>

<style>
hr.divider {
  border: none;
  border-top: 1px solid var(--border);
  margin: 0 3rem;
}

@media (max-width: 1024px) {
  hr.divider { margin: 0 2.5rem; }
}

@media (max-width: 700px) {
  hr.divider { margin: 0 1.5rem; }
}
</style>
