<template>
  <footer>
    <span class="copy">© 2026 Laura Nowak &nbsp;·&nbsp; Montaż Wideo &amp; Operator Kamery</span>

    <div class="footer-social">
      <a href="#" class="social-link" aria-label="YouTube" target="_blank" rel="noopener">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
          <path d="M22.54 6.42a2.78 2.78 0 0 0-1.95-1.97C18.88 4 12 4 12 4s-6.88 0-8.59.45A2.78 2.78 0 0 0 1.46 6.42 29 29 0 0 0 1 12a29 29 0 0 0 .46 5.58 2.78 2.78 0 0 0 1.95 1.97C5.12 20 12 20 12 20s6.88 0 8.59-.45a2.78 2.78 0 0 0 1.95-1.97A29 29 0 0 0 23 12a29 29 0 0 0-.46-5.58z"/>
          <polygon points="9.75 15.02 15.5 12 9.75 8.98 9.75 15.02" fill="currentColor" stroke="none"/>
        </svg>
      </a>
      <a href="#" class="social-link" aria-label="Instagram" target="_blank" rel="noopener">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
          <rect x="2" y="2" width="20" height="20" rx="5"/>
          <circle cx="12" cy="12" r="4.5"/>
          <circle cx="17.5" cy="6.5" r="0.8" fill="currentColor" stroke="none"/>
        </svg>
      </a>
    </div>

    <span class="copy copy-right">DaVinci Resolve Studio</span>
  </footer>
</template>

<style scoped>
footer {
  padding: 1.4rem 3rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-top: 1px solid var(--border);
  background: var(--bg);
  gap: 1rem;
}

.copy {
  font-size: 0.58rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--muted);
  opacity: 0.5;
}

.footer-social {
  display: flex;
  gap: 1rem;
  align-items: center;
}

.social-link {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  color: var(--muted);
  opacity: 0.4;
  transition: opacity 0.2s, color 0.2s;
}

.social-link:hover {
  opacity: 1;
  color: var(--accent);
}

.social-link svg {
  width: 16px;
  height: 16px;
}

@media (max-width: 700px) {
  footer {
    padding: 1.4rem 1.5rem;
    flex-direction: column;
    gap: 0.8rem;
    text-align: center;
  }
  .copy-right { display: none; }
}
</style>
