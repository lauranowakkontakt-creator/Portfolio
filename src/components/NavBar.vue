<template>
  <nav class="lf-nav">
    <a href="#" class="nav-logo" @click.prevent="close">
      <svg class="logo-icon" viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
        <circle cx="30" cy="30" r="26" fill="none" stroke="#EDEAE5" stroke-width="1.5"/>
        <g stroke="#C94B28" stroke-width="1.4" fill="none" stroke-linecap="round">
          <path d="M 30 4 L 43 22" />
          <path d="M 52.5 17 L 38 34.5" />
          <path d="M 52.5 43 L 30 43" />
          <path d="M 30 56 L 17 38" />
          <path d="M 7.5 43 L 22 25.5" />
          <path d="M 7.5 17 L 30 17" />
        </g>
        <circle cx="30" cy="30" r="3" fill="#C94B28"/>
      </svg>
      <div class="logo-wordmark">
        <span class="wm-name">LAURA NOWAK</span>
        <span class="wm-role">FILM · EDIT</span>
      </div>
    </a>

    <ul class="nav-links">
      <li><a href="#portfolio">Portfolio</a></li>
      <li><a href="#about">O mnie</a></li>
      <li><a href="#services">Doświadczenie</a></li>
      <li><a href="#contact">Kontakt</a></li>
    </ul>

    <button
      class="hamburger"
      :class="{ open: menuOpen }"
      @click="toggle"
      aria-label="Menu"
    >
      <span class="hb-line"></span>
      <span class="hb-line"></span>
    </button>
  </nav>

  <Transition name="overlay">
    <div v-if="menuOpen" class="mobile-overlay" @click.self="close">
      <nav class="mobile-nav">
        <ul>
          <li v-for="(link, i) in links" :key="link.href" :style="{ transitionDelay: menuOpen ? `${i * 55 + 80}ms` : '0ms' }" class="mobile-nav-item" :class="{ visible: menuOpen }">
            <a :href="link.href" @click="close">{{ link.label }}</a>
          </li>
        </ul>
      </nav>
    </div>
  </Transition>
</template>

<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

const links = [
  { href: '#portfolio', label: 'Portfolio' },
  { href: '#about',     label: 'O mnie' },
  { href: '#services',  label: 'Doświadczenie' },
  { href: '#contact',   label: 'Kontakt' },
]

function toggle() {
  menuOpen.value = !menuOpen.value
  document.body.style.overflow = menuOpen.value ? 'hidden' : ''
}

function close() {
  menuOpen.value = false
  document.body.style.overflow = ''
}
</script>

<style scoped>
.lf-nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 200;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 3rem;
  background: rgba(8,8,8,0.85);
  backdrop-filter: blur(28px);
  -webkit-backdrop-filter: blur(28px);
  border-bottom: 1px solid var(--border);
}

/* ── Logo ── */
.nav-logo {
  display: flex;
  align-items: center;
  gap: 0.85rem;
  text-decoration: none;
}

.logo-icon {
  width: 32px;
  height: 32px;
  flex-shrink: 0;
  transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.nav-logo:hover .logo-icon {
  transform: rotate(60deg);
}

.logo-wordmark {
  display: flex;
  flex-direction: column;
  gap: 2px;
  line-height: 1;
}

.wm-name {
  font-family: var(--font-display);
  font-size: 1rem;
  letter-spacing: 0.12em;
  color: var(--text);
  transition: color 0.3s;
}

.nav-logo:hover .wm-name {
  color: var(--accent2);
}

.wm-role {
  font-size: 0.56rem;
  letter-spacing: 0.24em;
  text-transform: uppercase;
  color: var(--muted);
}

/* ── Desktop links ── */
.nav-links {
  display: flex;
  gap: 2.5rem;
  list-style: none;
}

.nav-links a {
  position: relative;
  font-size: 0.66rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.25s ease;
  padding-bottom: 4px;
}

.nav-links a::after {
  content: '';
  position: absolute;
  left: 0; right: 0; bottom: 0;
  height: 1px;
  background: var(--accent);
  transform: scaleX(0);
  transform-origin: right;
  transition: transform 0.35s cubic-bezier(0.7, 0, 0.2, 1);
}

.nav-links a:hover { color: var(--text); }
.nav-links a:hover::after { transform: scaleX(1); transform-origin: left; }

/* ── Hamburger ── */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: center;
  align-items: flex-end;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 6px;
  z-index: 210;
}

.hb-line {
  display: block;
  height: 1.5px;
  background: var(--text);
  border-radius: 1px;
  transition: transform 0.35s cubic-bezier(0.4,0,0.2,1),
              opacity 0.25s,
              width 0.3s;
}

.hb-line:nth-child(1) { width: 22px; }
.hb-line:nth-child(2) { width: 16px; }

.hamburger:hover .hb-line:nth-child(2) { width: 22px; }

.hamburger.open .hb-line:nth-child(1) {
  width: 22px;
  transform: translateY(3.25px) rotate(45deg);
}
.hamburger.open .hb-line:nth-child(2) {
  width: 22px;
  transform: translateY(-3.25px) rotate(-45deg);
}

/* ── Mobile overlay ── */
.mobile-overlay {
  position: fixed;
  inset: 0;
  z-index: 190;
  background: rgba(8,8,8,0.97);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  display: flex;
  align-items: center;
  justify-content: center;
}

.mobile-nav ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
  text-align: center;
}

.mobile-nav-item {
  opacity: 0;
  transform: translateY(18px);
  transition: opacity 0.45s cubic-bezier(0.22,1,0.36,1),
              transform 0.45s cubic-bezier(0.22,1,0.36,1);
}
.mobile-nav-item.visible {
  opacity: 1;
  transform: translateY(0);
}

.mobile-nav a {
  display: block;
  font-family: var(--font-display);
  font-size: clamp(2.4rem, 8vw, 3.5rem);
  letter-spacing: 0.08em;
  color: var(--text);
  text-decoration: none;
  padding: 0.5rem 2rem;
  transition: color 0.2s;
}

.mobile-nav a:hover { color: var(--accent); }

/* ── Vue transitions ── */
.overlay-enter-active,
.overlay-leave-active {
  transition: opacity 0.3s ease;
}
.overlay-enter-from,
.overlay-leave-to {
  opacity: 0;
}

/* ── Responsive ── */
@media (max-width: 768px) {
  .lf-nav { padding: 0.9rem 1.5rem; }
  .logo-wordmark { display: none; }
  .nav-links { display: none; }
  .hamburger { display: flex; }
}
</style>
