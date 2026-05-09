<template>
  <section class="hero">

    <div class="hero-left">
      <p class="eyebrow reveal">
        <span class="eyebrow-line"></span>
        Operatorka Kamery&nbsp;·&nbsp;Montażystka Wideo&nbsp;·&nbsp;Gliwice &amp; Śląsk
      </p>

      <h1 class="reveal reveal-delay-1">
        LAURA<br>
        <span class="outline-word">NOWAK</span>
      </h1>

      <p class="hero-tagline reveal reveal-delay-1">Obraz, który ma znaczenie.</p>

      <p class="hero-desc reveal reveal-delay-2">
        Łączę techniczny warsztat z intuicją. Realizuję produkcje od kameralnych
        form po duże eventy, dbając o to, by efekt końcowy nie tylko dobrze
        wyglądał, ale przede wszystkim – opowiadał historię.
      </p>

      <div class="hero-actions reveal reveal-delay-3">
        <a href="#portfolio" class="btn-primary">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="white"><path d="M8 5v14l11-7z"/></svg>
          Moje prace
        </a>
        <a href="#contact" class="btn-ghost">Napisz do mnie</a>
      </div>

      <div class="hero-stats reveal reveal-delay-4">
        <div v-for="(s, i) in stats" :key="s.label" class="stat-item">
          <div v-if="i > 0" class="stat-sep"></div>
          <div class="stat">
            <span class="stat-num">{{ s.num }}</span>
            <span class="stat-label">{{ s.label }}</span>
          </div>
        </div>
      </div>
    </div>

    <div class="hero-right">
      <img
        :src="photoUrl"
        alt="Laura Nowak z kamerą na planie"
        @load="imgLoaded = true"
        :class="{ loaded: imgLoaded }"
      />
    </div>

    <div class="scroll-hint">
      <div class="scroll-line"></div>
      scroll
    </div>

  </section>
</template>

<script setup>
import { ref } from 'vue'

const imgLoaded = ref(false)
const photoUrl = import.meta.env.BASE_URL + 'photo.jpg'

const stats = [
  { num: '7', label: 'lat za kamerą' },
  { num: '6', label: 'lat w montażu' },
  { num: '200+', label: 'domkniętych projektów' },
]
</script>

<style scoped>
.hero {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 100vh;
  position: relative;
  overflow: hidden;
}

/* ── LEFT ── */
.hero-left {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 5.5rem 3.5rem 2.5rem 3rem;
  position: relative;
  z-index: 2;
}

.eyebrow {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 0.6rem;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: var(--accent2);
  margin-bottom: 1rem;
}

.eyebrow-line {
  width: 24px;
  height: 1px;
  background: var(--accent2);
  opacity: 0.7;
  flex-shrink: 0;
}

h1 {
  font-family: var(--font-display);
  font-size: clamp(3.8rem, 6.5vw, 6rem);
  line-height: 0.9;
  letter-spacing: 0.03em;
  color: var(--text);
  margin-bottom: 0.7rem;
}

.outline-word {
  color: transparent;
  -webkit-text-stroke: 1.5px rgba(237,234,229,0.35);
}

.hero-tagline {
  font-size: 0.97rem;
  font-weight: 300;
  font-style: italic;
  color: var(--text);
  opacity: 0.7;
  margin-bottom: 1rem;
  letter-spacing: 0.01em;
}

.hero-desc {
  font-size: 0.88rem;
  color: var(--muted);
  line-height: 1.8;
  max-width: 420px;
  margin-bottom: 1.8rem;
  font-weight: 300;
}

.hero-actions {
  display: flex;
  gap: 1.2rem;
  align-items: center;
  margin-bottom: 2rem;
}

.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 0.55rem;
  background: var(--accent);
  color: #fff;
  padding: 0.85rem 2rem;
  text-decoration: none;
  font-family: var(--font-display);
  font-size: 0.9rem;
  letter-spacing: 0.12em;
  transition: background 0.2s, transform 0.2s;
}

.btn-primary:hover {
  background: var(--accent2);
  transform: translateY(-1px);
}

.btn-ghost {
  color: rgba(237,234,229,0.5);
  text-decoration: none;
  font-size: 0.66rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  border-bottom: 1px solid rgba(237,234,229,0.2);
  padding-bottom: 2px;
  transition: color 0.2s, border-color 0.2s;
}

.btn-ghost:hover {
  color: var(--text);
  border-color: rgba(237,234,229,0.5);
}

/* Stats */
.hero-stats {
  display: flex;
  align-items: center;
  gap: 0;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(237,234,229,0.1);
}

.stat-item {
  display: flex;
  align-items: center;
}

.stat {
  display: flex;
  flex-direction: column;
  gap: 3px;
  padding: 0 2rem 0 0;
}

.stat-item:first-child .stat { padding-left: 0; }

.stat-num {
  font-family: var(--font-display);
  font-size: 1.8rem;
  color: var(--text);
  letter-spacing: 0.04em;
  line-height: 1;
}

.stat-label {
  font-size: 0.58rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--muted);
}

.stat-sep {
  width: 1px;
  height: 2rem;
  background: rgba(237,234,229,0.1);
  align-self: center;
  margin-right: 2rem;
}

/* ── RIGHT (photo) ── */
.hero-right {
  position: relative;
  overflow: hidden;
}

.hero-right img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 60% 15%;
  display: block;
  filter: grayscale(12%) brightness(0.85);
  transform: scale(1.04);
  transition: transform 8s ease-out;
}

.hero-right img.loaded { transform: scale(1); }

.hero-right::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to right, var(--bg) 0%, transparent 40%);
  z-index: 1;
}

.hero-right::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, var(--bg) 0%, transparent 25%);
  z-index: 1;
}

/* ── Scroll hint ── */
.scroll-hint {
  position: absolute;
  bottom: 2rem;
  right: 3rem;
  z-index: 3;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.55rem;
  letter-spacing: 0.26em;
  text-transform: uppercase;
  color: var(--muted);
}

.scroll-line {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, var(--muted), transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}

@keyframes scrollPulse {
  0%, 100% { opacity: 0.4; transform: scaleY(1); }
  50% { opacity: 1; transform: scaleY(0.7); }
}

/* ── Responsive ── */
@media (max-width: 860px) {
  .hero { grid-template-columns: 1fr; }
  .hero-right { height: 65vw; order: -1; }
  .hero-right::before {
    background: linear-gradient(to bottom, transparent 40%, var(--bg) 100%);
  }
  .hero-right::after { display: none; }
  .hero-left { padding: 2.5rem 1.5rem 3rem; }
  .scroll-hint { display: none; }
}

@media (max-width: 480px) {
  h1 { font-size: clamp(3.5rem, 16vw, 5rem); }
  .hero-stats { flex-wrap: wrap; gap: 1rem; }
  .stat-sep { display: none; }
  .stat { padding: 0 1.5rem 0 0; }
}
</style>
