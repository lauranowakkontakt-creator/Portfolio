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

      <p class="hero-tagline reveal reveal-delay-1">Kamera, montaż, historia.</p>

      <p class="hero-desc reveal reveal-delay-2">
        Kamerą zajmuję się od 7 lat, montażem od 6. W tym czasie zrobiłam
        ponad 200 projektów — wesela, studniówki, teledyski, podcasty.
        Lubię, kiedy film coś mówi, nie tylko dobrze wygląda.
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
      <div class="hero-photo-frame">
        <img
          :src="photoUrl"
          alt="Laura Nowak z kamerą na planie"
          @load="imgLoaded = true"
        />
        <span class="corners"><span></span></span>
        <div class="hero-rec">REC</div>
      </div>
      <div class="hero-timecode"><span class="tc-dot"></span>00:07:42</div>
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
  { num: '7',    label: 'lat za kamerą' },
  { num: '6',    label: 'lat w montażu' },
  { num: '200+', label: 'domkniętych projektów' },
]
</script>

<style scoped>
.hero {
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
  min-height: 92vh;
  position: relative;
  overflow: hidden;
  gap: 2.5rem;
  align-items: center;
  padding: 5rem 3rem 3rem;
}

/* ── LEFT ── */
.hero-left {
  display: flex;
  flex-direction: column;
  justify-content: center;
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
  position: relative;
  overflow: hidden;
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

.btn-primary::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(120deg, transparent 0%, rgba(255,255,255,0.25) 50%, transparent 100%);
  transform: translateX(-110%);
  transition: transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.btn-primary:hover {
  background: var(--accent2);
  transform: translateY(-2px);
  box-shadow: 0 12px 32px -8px rgba(201,75,40,0.5);
}

.btn-primary:hover::before { transform: translateX(110%); }

.btn-primary > * { position: relative; z-index: 1; }

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
  align-self: center;
  justify-self: end;
  width: 100%;
  max-width: 440px;
  aspect-ratio: 3 / 4;
}

/* decorative offset frame behind photo */
.hero-right::before {
  content: '';
  position: absolute;
  top: 16px; left: 16px; right: -16px; bottom: -16px;
  border: 1px solid var(--accent);
  opacity: 0.4;
  z-index: -1;
  transition: transform 0.6s cubic-bezier(0.4,0,0.2,1), opacity 0.4s;
}

.hero-right:hover::before { transform: translate(6px, 6px); opacity: 0.7; }

.hero-photo-frame {
  position: absolute;
  inset: 0;
  overflow: hidden;
  border: 1px solid var(--border2);
  box-shadow: 0 40px 90px -25px rgba(0,0,0,0.7),
              0 0 0 1px rgba(201,75,40,0.06),
              inset 0 0 120px rgba(0,0,0,0.4);
}

.hero-photo-frame img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 50% 25%;
  display: block;
  filter: grayscale(20%) brightness(0.92) contrast(1.08);
  transition: filter 0.6s ease;
}

.hero-right:hover .hero-photo-frame img {
  filter: grayscale(0%) brightness(1) contrast(1.1);
}

/* duotone film overlay */
.hero-photo-frame::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(201,75,40,0.06) 0%, transparent 30%, transparent 70%, rgba(8,8,8,0.4) 100%);
  pointer-events: none;
}

/* REC indicator */
.hero-rec {
  position: absolute;
  top: 14px; left: 14px;
  z-index: 4;
  font-family: var(--font-display);
  font-size: 0.7rem;
  letter-spacing: 0.2em;
  color: var(--accent);
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

.hero-rec::before {
  content: '';
  width: 8px; height: 8px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 12px rgba(201,75,40,0.9);
  animation: recPulse 1.6s ease-in-out infinite;
}

@keyframes recPulse {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.3; }
}

/* timecode chip */
.hero-timecode {
  position: absolute;
  bottom: -10px; right: -10px;
  background: var(--bg);
  border: 1px solid var(--accent);
  padding: 0.55rem 0.85rem;
  font-family: var(--font-display);
  font-size: 0.72rem;
  letter-spacing: 0.22em;
  color: var(--accent2);
  z-index: 4;
  display: flex;
  align-items: center;
  gap: 0.55rem;
}

.tc-dot {
  width: 7px; height: 7px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 10px rgba(201,75,40,0.9);
  animation: recPulse 1.6s ease-in-out infinite;
}

/* Corner crop marks */
.hero-photo-frame .corners::before,
.hero-photo-frame .corners::after,
.hero-photo-frame .corners > span::before,
.hero-photo-frame .corners > span::after {
  content: '';
  position: absolute;
  width: 14px;
  height: 14px;
  border-color: var(--accent);
  border-style: solid;
  z-index: 3;
}

.hero-photo-frame .corners::before  { top: 8px;    left: 8px;  border-width: 1.5px 0 0 1.5px; }
.hero-photo-frame .corners::after   { top: 8px;    right: 8px; border-width: 1.5px 1.5px 0 0; }
.hero-photo-frame .corners > span::before { bottom: 8px; left: 8px;  border-width: 0 0 1.5px 1.5px; }
.hero-photo-frame .corners > span::after  { bottom: 8px; right: 8px; border-width: 0 1.5px 1.5px 0; }

.hero-photo-frame .corners > span {
  position: absolute;
  inset: 0;
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
  .hero {
    grid-template-columns: 1fr;
    padding: 4rem 1.5rem 2.5rem;
    gap: 2rem;
  }
  .hero-right {
    order: -1;
    max-width: 300px;
    aspect-ratio: 3 / 4;
    justify-self: center;
  }
  .scroll-hint { display: none; }
}

@media (max-width: 480px) {
  h1 { font-size: clamp(3.5rem, 16vw, 5rem); }
  .hero-stats { flex-wrap: wrap; gap: 1rem; }
  .stat-sep { display: none; }
  .stat { padding: 0 1.5rem 0 0; }
}
</style>
