<template>
  <section class="hero">

    <div class="hero-content">
      <p class="eyebrow">
        <span>Montaż&nbsp;Wideo</span>
        <span class="sep">·</span>
        <span>Operator&nbsp;Kamery</span>
      </p>

      <h1>
        <span class="line-solid">Laura</span>
        <span class="line-outline">Nowak</span>
      </h1>

      <p class="desc">
        Tworzę filmy, które zatrzymują emocje.<br>
        Znam tę pracę z obu stron kamery.
      </p>

      <div class="cta">
        <a href="#portfolio" class="btn-primary">Zobacz prace</a>
        <a href="#contact" class="btn-ghost">Napisz do mnie</a>
      </div>
    </div>

    <div class="stats-bar">
      <div class="stat">
        <span class="stat-num">6</span>
        <span class="stat-label">lat w montażu</span>
      </div>
      <div class="stat-divider"></div>
      <div class="stat">
        <span class="stat-num">7</span>
        <span class="stat-label">lat za kamerą</span>
      </div>
      <div class="stat-divider"></div>
      <div class="stat">
        <span class="stat-num">100+</span>
        <span class="stat-label">projektów wideo</span>
      </div>
    </div>

  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  padding: 0 4rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.hero-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding-top: 7rem;
  padding-bottom: 3rem;
}

.eyebrow {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  font-size: 0.7rem;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 2rem;
}

.sep {
  opacity: 0.35;
}

h1 {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: clamp(5.5rem, 13vw, 12rem);
  line-height: 0.88;
  letter-spacing: -0.03em;
  margin-bottom: 2.5rem;
  display: flex;
  flex-direction: column;
}

.line-solid {
  color: var(--text);
}

/* "NOWAK" jako tekst konturowy (outline) — efekt typograficzny */
.line-outline {
  color: transparent;
  -webkit-text-stroke: 2px var(--text);
}

.desc {
  font-size: 1rem;
  color: var(--muted);
  line-height: 1.75;
  max-width: 400px;
  margin-bottom: 2.5rem;
}

.cta {
  display: flex;
  gap: 1.2rem;
  align-items: center;
}

.btn-primary {
  display: inline-block;
  background: var(--accent);
  color: #fff;
  padding: 0.9rem 2.2rem;
  text-decoration: none;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  transition: opacity 0.2s;
}

.btn-primary:hover {
  opacity: 0.85;
}

.btn-ghost {
  color: var(--muted);
  text-decoration: none;
  font-size: 0.72rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  transition: color 0.2s;
  border-bottom: 1px solid rgba(106, 101, 96, 0.4);
  padding-bottom: 2px;
}

.btn-ghost:hover {
  color: var(--text);
  border-color: var(--text);
}

/* Pasek statystyk na dole */
.stats-bar {
  display: flex;
  align-items: center;
  gap: 2.5rem;
  padding: 2rem 0;
  border-top: 1px solid var(--border);
}

.stat {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.stat-num {
  font-family: var(--font-display);
  font-weight: 700;
  font-size: 2rem;
  color: var(--text);
  line-height: 1;
}

.stat-label {
  font-size: 0.65rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--muted);
}

.stat-divider {
  width: 1px;
  height: 2rem;
  background: var(--border);
}

@media (max-width: 1024px) {
  .hero { padding: 0 2.5rem; }
}

@media (max-width: 700px) {
  .hero { padding: 0 1.5rem; }
  h1 { font-size: clamp(4rem, 18vw, 6rem); }
  .line-outline { -webkit-text-stroke-width: 1.5px; }
  .stats-bar { gap: 1.5rem; flex-wrap: wrap; }
}
</style>
