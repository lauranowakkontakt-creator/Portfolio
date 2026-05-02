<template>
  <section class="about" id="about">
    <div class="about-inner">
      <p class="section-label">O mnie</p>
      <h2>Znam tę pracę z obu stron kamery</h2>
      <p>
        Montuję wideo od 6 lat i przez 7 lat pracowałam jako operatorka kamery.
        Dzięki temu rozumiem nie tylko to, co dzieje się podczas montażu, ale też
        jak wygląda praca na planie i co jest w nagrywaniu naprawdę trudne.
      </p>
      <p>
        Specjalizuję się w teledyskach ślubnych, filmach weselnych, nagraniach
        muzycznych i podcastach. Bez problemu dostosuję się do Twojego stylu i wizji,
        jestem elastyczna i otwarta na różne pomysły.
      </p>
      <div class="tool-pill">
        <svg viewBox="0 0 24 24" width="13" height="13" fill="var(--accent)"><path d="M8 5v14l11-7z"/></svg>
        Pracuję w <strong>DaVinci Resolve Studio</strong>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 5rem 4rem;
  background: var(--surface);
}

.about-inner {
  max-width: 720px;
}

.section-label {
  font-size: 0.68rem;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 1.2rem;
}

h2 {
  font-family: var(--font-display);
  font-weight: 700;
  font-size: clamp(1.8rem, 3.5vw, 2.8rem);
  color: var(--text);
  letter-spacing: -0.02em;
  line-height: 1.1;
  margin-bottom: 1.8rem;
}

p {
  font-size: 0.97rem;
  color: var(--muted);
  line-height: 1.85;
  margin-bottom: 0.9rem;
}

p:last-of-type {
  margin-bottom: 0;
}

.tool-pill {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: var(--bg);
  border: 1px solid var(--border);
  padding: 0.5rem 1rem;
  font-size: 0.75rem;
  letter-spacing: 0.04em;
  color: var(--muted);
  margin-top: 1.8rem;
}

.tool-pill strong {
  color: var(--text);
  font-weight: 500;
}

@media (max-width: 1024px) {
  .about { padding-left: 2.5rem; padding-right: 2.5rem; }
}

@media (max-width: 700px) {
  .about { padding-left: 1.5rem; padding-right: 1.5rem; }
}
</style>
