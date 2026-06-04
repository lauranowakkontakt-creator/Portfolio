<template>
  <section class="about" id="about">
    <div class="about-inner">
      <div class="about-grid">

        <div class="about-left">
          <p class="section-label reveal">O mnie</p>
          <h2 class="reveal reveal-delay-1">O mnie.</h2>
          <p class="lead reveal reveal-delay-2">
            Wszystko zaczęło się w czasie pandemii — gdy świat stanął w miejscu,
            wiele rzeczy przeniosło się do sieci i właśnie wtedy po raz pierwszy
            sięgnęłam po kamerę. Jakiś czas później pojawiła się potrzeba montażu
            i tak oto jestem tutaj.
          </p>
          <p class="lead lead-second reveal reveal-delay-2">
            Z natury jestem spokojna i cierpliwa, co bardzo pomaga mi w skupieniu
            się na detalach. Towarzyszy mi też naturalna ciekawość świata — lubię
            się uczyć i zagłębiać w tematy, które jeszcze są mi nieznane.
            Śledzę nowinki branżowe i chętnie sięgam po nowe narzędzia, w tym
            rozwiązania oparte na AI, które pozwalają mi pracować sprawniej.
          </p>
          <p class="lead lead-second reveal reveal-delay-2">
            Studiuję psychologię — i nie jest to przypadek. Lubię ludzi,
            interesują mnie ich historie i to, kim są. Najbardziej odpowiada mi
            bycie blisko drugiego człowieka i towarzyszenie mu w tym,
            z czym się mierzy.
          </p>

          <!-- Stats grid -->
          <div class="about-stats reveal reveal-delay-3">
            <div class="stat-cell">
              <span class="stat-num">6</span>
              <span class="stat-lbl">Lat w montażu</span>
            </div>
            <div class="stat-cell">
              <span class="stat-num">7</span>
              <span class="stat-lbl">Lat w kadrze</span>
            </div>
            <div class="stat-cell">
              <span class="stat-num">200<sup>+</sup></span>
              <span class="stat-lbl">Projektów</span>
            </div>
            <div class="stat-cell">
              <span class="stat-num">250<sup>+</sup></span>
              <span class="stat-lbl">Realizacji live</span>
            </div>
          </div>

          <!-- Skill bars -->
          <div class="skill-section reveal reveal-delay-4" ref="barsRef">
            <p class="skill-heading">Doświadczenie</p>
            <div class="skill-bars">
              <div v-for="skill in skills" :key="skill.label" class="skill-row">
                <span class="skill-name">{{ skill.label }}</span>
                <div class="skill-track">
                  <div
                    class="skill-fill"
                    :style="{ width: barsVisible ? skill.pct + '%' : '0%', transitionDelay: skill.delay }"
                  ></div>
                </div>
                <span class="skill-yrs">{{ skill.years }}</span>
              </div>
            </div>
          </div>

        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const barsRef = ref(null)
const barsVisible = ref(false)

const skills = [
  { label: 'Operator kamery',  years: '7 lat', pct: 100, delay: '0ms'   },
  { label: 'Montaż wideo',     years: '6 lat', pct: 86,  delay: '100ms' },
  { label: 'Color grading',    years: '5 lat', pct: 71,  delay: '200ms' },
  { label: 'Eventy & live',    years: '4 lat', pct: 57,  delay: '300ms' },
]

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        barsVisible.value = true
        observer.disconnect()
      }
    },
    { threshold: 0.4 }
  )
  if (barsRef.value) observer.observe(barsRef.value)
})
</script>

<style scoped>
.about {
  padding: 5rem 3rem;
  background: var(--surface);
  position: relative;
  overflow: hidden;
}

.about::before {
  content: '';
  position: absolute;
  top: 0; right: 0;
  width: 40%; height: 100%;
  background:
    repeating-linear-gradient(0deg, transparent 0 18px, rgba(201,75,40,0.04) 18px 19px),
    radial-gradient(ellipse at top right, rgba(201,75,40,0.08) 0%, transparent 60%);
  pointer-events: none;
}

.about-inner {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr;
  max-width: 720px;
}

.section-label {
  font-size: 0.6rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: var(--accent2);
  margin-bottom: 1rem;
}

h2 {
  font-family: var(--font-display);
  font-size: clamp(2.4rem, 4.5vw, 3.8rem);
  letter-spacing: 0.05em;
  color: var(--text);
  line-height: 0.95;
  margin-bottom: 2rem;
  position: relative;
  display: inline-block;
}

h2::after {
  content: '';
  position: absolute;
  left: 0; bottom: -10px;
  width: 48px; height: 2px;
  background: var(--accent);
  transform-origin: left;
  animation: lineGrow 1.2s 0.3s cubic-bezier(0.2, 0.7, 0.2, 1) both;
}

@keyframes lineGrow {
  from { transform: scaleX(0); }
  to   { transform: scaleX(1); }
}

.lead {
  font-size: 0.92rem;
  color: var(--muted);
  line-height: 1.85;
  max-width: 540px;
  margin-bottom: 1.2rem;
  font-weight: 300;
}

.lead-second {
  margin-bottom: 1.2rem;
}

.lead:last-of-type {
  margin-bottom: 2.4rem;
}

/* ── Stats grid ── */
.about-stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  margin-top: 1rem;
}

.stat-cell {
  padding: 1.2rem 0;
  text-align: left;
  border-right: 1px solid var(--border);
  transition: background 0.3s;
}

.stat-cell:last-child { border-right: none; padding-left: 1.2rem; }
.stat-cell:not(:first-child):not(:last-child) { padding-left: 1.2rem; }
.stat-cell:hover { background: rgba(201,75,40,0.05); }

.stat-num {
  font-family: var(--font-display);
  font-size: 2.2rem;
  color: var(--accent);
  letter-spacing: 0.04em;
  line-height: 1;
  display: block;
  margin-bottom: 0.4rem;
}

.stat-num sup {
  font-size: 1rem;
  vertical-align: super;
  color: var(--accent2);
}

.stat-lbl {
  font-family: var(--font-body);
  font-size: 0.6rem;
  letter-spacing: 0.26em;
  text-transform: uppercase;
  color: var(--muted);
}

/* ── Skill bars ── */
.skill-section {
  margin-top: 2.8rem;
}

.skill-heading {
  font-size: 0.58rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: var(--muted);
  margin-bottom: 1.4rem;
  opacity: 0.6;
}

.skill-bars {
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
}

.skill-row {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.skill-name {
  font-family: var(--font-display);
  font-size: 0.78rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text);
  width: 160px;
  flex-shrink: 0;
  line-height: 1;
}

.skill-track {
  flex: 1;
  height: 2px;
  background: var(--border2);
  position: relative;
  overflow: hidden;
}

.skill-fill {
  position: absolute;
  left: 0; top: 0;
  height: 100%;
  background: linear-gradient(to right, var(--accent), var(--accent2));
  transition: width 1.5s cubic-bezier(0.22, 1, 0.36, 1);
}

.skill-yrs {
  font-size: 0.62rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--muted);
  width: 42px;
  text-align: right;
  flex-shrink: 0;
  font-variant-numeric: tabular-nums;
}

/* ── Responsive ── */
@media (max-width: 1024px) {
  .about { padding-left: 2.5rem; padding-right: 2.5rem; }
}

@media (max-width: 700px) {
  .about { padding-left: 1.5rem; padding-right: 1.5rem; }

  /* 2×2 grid for stats on mobile */
  .about-stats {
    grid-template-columns: 1fr 1fr;
  }
  .stat-cell {
    border-right: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 1rem 0.8rem !important;
  }
  .stat-cell:nth-child(2),
  .stat-cell:nth-child(4) {
    border-right: none;
  }
  .stat-cell:nth-child(3),
  .stat-cell:nth-child(4) {
    border-bottom: none;
  }

  .skill-name { width: 130px; font-size: 0.7rem; }
}

@media (max-width: 400px) {
  .skill-name { width: 110px; font-size: 0.65rem; }
  .skill-yrs  { width: 34px; font-size: 0.58rem; }
}
</style>
