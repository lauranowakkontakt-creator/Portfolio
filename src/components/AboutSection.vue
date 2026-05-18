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
          <div class="about-stats reveal reveal-delay-3">
            <div class="stat-cell">
              <span class="stat-num">200<sup>+</sup></span>
              <span class="stat-lbl">Projektów</span>
            </div>
            <div class="stat-cell">
              <span class="stat-num">7</span>
              <span class="stat-lbl">Lat w kadrze</span>
            </div>
            <div class="stat-cell">
              <span class="stat-num">6</span>
              <span class="stat-lbl">Lat w montażu</span>
            </div>
          </div>
        </div>

        <div class="about-right">
          <div class="pillars-list">
            <div
              v-for="(pillar, i) in pillars"
              :key="pillar.title"
              class="pillar reveal"
              :class="`reveal-delay-${i + 1}`"
            >
              <span class="pillar-num">0{{ i + 1 }}</span>
              <div class="pillar-body">
                <p class="pillar-title">{{ pillar.title }}</p>
                <p class="pillar-text">{{ pillar.text }}</p>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
const pillars = [
  {
    title: 'Atmosfera i komunikacja',
    text: 'Po prostu lubię ludzi. Dbam o to, żeby każdy przed kamerą czuł się swobodnie, bo brak spiny od razu widać w naturalnych ujęciach. W zespole cenię czyste zasady i terminowość.',
  },
  {
    title: 'DaVinci Resolve Studio',
    text: 'To moje główne środowisko pracy od lat. Montaż, dźwięk i color grading robię w jednym miejscu, więc traktuję kolor bardzo poważnie. Narzędzia AI wdrażam na bieżąco, ale tylko jako asystenta do nudnych, technicznych zadań.',
  },
  {
    title: 'Elastyczne podejście',
    text: 'Nie pracuję z gotowymi szablonami. Dynamiczny teledysk, kilkudniowy festiwal czy podcast wymagają zupełnie innego języka wizualnego. Jeśli Twój projekt potrzebuje stylu, którego nie ma w moim portfolio — chętnie wejdę w coś nowego.',
  },
]
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
  grid-template-columns: 1.05fr 1fr;
  gap: 4rem;
  align-items: start;
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


.about-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
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

/* Pillars */
.pillars-list {
  display: flex;
  flex-direction: column;
  gap: 1px;
  background: var(--border);
}

.pillar {
  background: var(--surface);
  padding: 1.6rem 1.6rem 1.6rem 1.8rem;
  position: relative;
  transition: background 0.4s, padding-left 0.4s;
  cursor: default;
  display: grid;
  grid-template-columns: 36px 1fr;
  gap: 1rem;
  align-items: start;
}

.pillar::before {
  content: '';
  position: absolute;
  left: 0; top: 0; bottom: 0;
  width: 2px;
  background: var(--accent);
  transform: scaleY(0);
  transform-origin: top;
  transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.pillar:hover { background: var(--bg); padding-left: 2.1rem; }
.pillar:hover::before { transform: scaleY(1); }
.pillar:hover .pillar-num { color: var(--accent2); }
.pillar:hover .pillar-title { color: var(--accent); }

.pillar-num {
  font-family: var(--font-display);
  font-size: 1.05rem;
  color: var(--accent);
  letter-spacing: 0.08em;
  line-height: 1;
  padding-top: 4px;
  transition: color 0.3s;
}

.pillar-body { min-width: 0; }

.pillar-title {
  font-family: var(--font-display);
  font-size: 1rem;
  font-weight: 400;
  color: var(--text);
  letter-spacing: 0.05em;
  text-transform: uppercase;
  margin-bottom: 0.55rem;
  line-height: 1.2;
  transition: color 0.3s;
}

.pillar-text {
  font-size: 0.82rem;
  color: var(--muted);
  line-height: 1.75;
  font-weight: 300;
}

@media (max-width: 1024px) {
  .about { padding-left: 2.5rem; padding-right: 2.5rem; }
  .about-grid { grid-template-columns: 1fr; gap: 3rem; }
}

@media (max-width: 700px) {
  .about { padding-left: 1.5rem; padding-right: 1.5rem; }
  .about-stats { grid-template-columns: 1fr; }
  .stat-cell {
    border-right: none;
    border-bottom: 1px solid var(--border);
    padding: 1rem 0 !important;
  }
  .stat-cell:last-child { border-bottom: none; }
  .pillar { grid-template-columns: 30px 1fr; padding: 1.3rem 1.2rem; }
  .pillar:hover { padding-left: 1.5rem; }
}
</style>
