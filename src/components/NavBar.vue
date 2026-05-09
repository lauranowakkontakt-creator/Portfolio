<template>
  <nav>
    <a href="#" class="nav-logo">
      <svg class="logo-icon" viewBox="0 0 34 34" fill="none" xmlns="http://www.w3.org/2000/svg">
        <circle cx="17" cy="17" r="16" stroke="var(--accent)" stroke-width="1.5"/>
        <circle cx="17" cy="17" r="10" stroke="var(--accent)" stroke-width="1" opacity="0.5"/>
        <circle cx="17" cy="17" r="6" fill="var(--accent)" opacity="0.15"/>
        <path d="M14.5 13.5L22 17L14.5 20.5V13.5Z" fill="var(--accent)"/>
      </svg>
      <div class="logo-wordmark">
        <span class="wm-name">LAURA NOWAK</span>
        <span class="wm-role">Operatorka · Montażystka</span>
      </div>
    </a>
    <ul class="nav-links">
      <li><a href="#portfolio">Portfolio</a></li>
      <li><a href="#about">O mnie</a></li>
      <li><a href="#services">Usługi</a></li>
      <li><a href="#contact">Kontakt</a></li>
    </ul>
  </nav>
</template>

<style scoped>
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 200;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 3rem;
  background: rgba(8, 8, 8, 0.8);
  backdrop-filter: blur(28px);
  -webkit-backdrop-filter: blur(28px);
  border-bottom: 1px solid var(--border);
}

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
}

.wm-role {
  font-size: 0.56rem;
  letter-spacing: 0.24em;
  text-transform: uppercase;
  color: var(--muted);
}

.nav-links {
  display: flex;
  gap: 2.5rem;
  list-style: none;
}

.nav-links a {
  font-size: 0.66rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.2s;
}

.nav-links a:hover { color: var(--text); }

@media (max-width: 768px) {
  nav { padding: 0.9rem 1.5rem; }
  .logo-wordmark { display: none; }
  .nav-links { gap: 1.5rem; }
}

@media (max-width: 480px) {
  .nav-links li:nth-child(3) { display: none; }
}
</style>
