<template>
  <nav>
    <a href="#" class="nav-brand">
      <LogoMark />
      <span class="nav-name">Laura Nowak</span>
    </a>
    <ul class="nav-links">
      <li><a href="#portfolio">Portfolio</a></li>
      <li><a href="#about">O mnie</a></li>
      <li><a href="#contact">Kontakt</a></li>
    </ul>
  </nav>
</template>

<script setup>
import LogoMark from './LogoMark.vue'
</script>

<style scoped>
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.2rem 4rem;
  background: rgba(13, 13, 13, 0.85);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
}

.nav-brand {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  text-decoration: none;
}

.nav-name {
  font-family: var(--font-display);
  font-size: 0.95rem;
  font-weight: 700;
  letter-spacing: 0.04em;
  color: var(--text);
}

.nav-links {
  display: flex;
  gap: 2.5rem;
  list-style: none;
}

.nav-links a {
  font-size: 0.72rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.25s;
}

.nav-links a:hover {
  color: var(--text);
}

@media (max-width: 700px) {
  nav { padding: 1rem 1.5rem; }
  .nav-name { display: none; }
  .nav-links { gap: 1.2rem; }
}
</style>
