<template>
  <footer>
    <span class="copy">© 2026 Laura Nowak &nbsp;·&nbsp; Montaż Wideo &amp; Operator Kamery</span>
    <span class="copy">DaVinci Resolve Studio</span>
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
}

.copy {
  font-size: 0.58rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--muted);
  opacity: 0.5;
}

@media (max-width: 700px) {
  footer {
    padding: 1.4rem 1.5rem;
    flex-direction: column;
    gap: 0.4rem;
    text-align: center;
  }
}
</style>
