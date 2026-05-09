<template>
  <section class="services" id="services">
    <div class="services-inner">

      <div class="services-head reveal">
        <div>
          <p class="section-label">W czym mogę Ci pomóc</p>
          <h2>Cztery obszary,<br>jeden warsztat.</h2>
        </div>
        <p class="services-tag">
          Od pierwszego briefu po finalny eksport — prowadzę projekt całościowo
          albo wchodzę w wybrany etap.
        </p>
      </div>

      <div class="services-grid">
        <div
          v-for="(service, i) in services"
          :key="service.title"
          class="service-card reveal"
          :class="`reveal-delay-${i + 1}`"
        >
          <div class="service-top">
            <span class="service-icon" v-html="service.icon"></span>
            <span class="service-num">{{ service.num }}</span>
          </div>
          <h3>{{ service.title }}</h3>
          <p>{{ service.desc }}</p>
        </div>
      </div>

      <div class="tools-row reveal reveal-delay-3">
        <span class="tools-label">W czym pracuję</span>
        <div class="tools-grid">
          <div class="tool-chip">
            <span class="davinci-mark">
              <svg width="22" height="22" viewBox="0 0 22 22" fill="none">
                <circle cx="11" cy="11" r="10" stroke="#C94B28" stroke-width="1.4"/>
                <path d="M11 1 a10 10 0 0 1 0 20" stroke="#E05E38" stroke-width="1.4" fill="none"/>
                <circle cx="11" cy="11" r="3.5" fill="#C94B28"/>
              </svg>
            </span>
            <span class="tool-name">
              <span class="tool-cat">Postprodukcja</span>
              DaVinci Resolve <small>Studio 19</small>
            </span>
          </div>
          <div class="tool-chip">
            <span class="davinci-mark"><span class="davinci-dot"></span></span>
            <span class="tool-name">
              <span class="tool-cat">Kamera</span>
              Panasonic Lumix <small>S5IIX</small>
            </span>
          </div>
          <div class="tool-chip">
            <span class="davinci-mark"><span class="davinci-dot" style="animation-delay: 0.2s"></span></span>
            <span class="tool-name">
              <span class="tool-cat">360°</span>
              Insta360 <small>X4</small>
            </span>
          </div>
          <div class="tool-chip">
            <span class="davinci-mark"><span class="davinci-dot" style="animation-delay: 0.4s"></span></span>
            <span class="tool-name">
              <span class="tool-cat">Obiektyw</span>
              Sigma 24-70mm <small>f/2.8 ART II</small>
            </span>
          </div>
          <div class="tool-chip">
            <span class="davinci-mark"><span class="davinci-dot" style="animation-delay: 0.6s"></span></span>
            <span class="tool-name">
              <span class="tool-cat">Światło</span>
              Nanlite Forza <small>60B II</small>
            </span>
          </div>
          <div class="tool-chip">
            <span class="davinci-mark"><span class="davinci-dot" style="animation-delay: 0.8s"></span></span>
            <span class="tool-name">
              <span class="tool-cat">Światło RGB</span>
              Nanlite Litolite <small>5C RGB</small>
            </span>
          </div>
          <div class="tool-chip">
            <span class="davinci-mark"><span class="davinci-dot" style="animation-delay: 1s"></span></span>
            <span class="tool-name">
              <span class="tool-cat">Światło</span>
              Nanlite Pavotube II <small>30C × 2</small>
            </span>
          </div>
          <div class="tool-chip">
            <span class="davinci-mark"><span class="davinci-dot" style="animation-delay: 1.2s"></span></span>
            <span class="tool-name">
              <span class="tool-cat">Workflow</span>
              AI Tools <small>Acceleration</small>
            </span>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
const services = [
  {
    num: '01',
    title: 'Produkcje Eventowe & Reportaże',
    desc: 'Studniówki, koncerty, wydarzenia firmowe. Pełna obsługa kamerowa od przygotowania po finalny montaż.',
    icon: `<svg viewBox="0 0 40 40" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><rect x="4" y="12" width="22" height="16" rx="1"/><path d="M26 18 L36 13 L36 27 L26 22 Z"/><circle cx="10" cy="20" r="2"/></svg>`,
  },
  {
    num: '02',
    title: 'Filmy Ślubne & Teledyski',
    desc: 'Emocje ujęte w nowoczesną formę. Dbam o każdy detal — od kompozycji kadru po rytm w montażu.',
    icon: `<svg viewBox="0 0 40 40" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><path d="M14 28 L14 14 a6 6 0 0 1 12 0 L26 28"/><path d="M10 28 L30 28"/><circle cx="20" cy="14" r="2.5"/><path d="M20 16.5 L20 22"/></svg>`,
  },
  {
    num: '03',
    title: 'Content Digitalowy',
    desc: 'Podcasty, nagrania muzyczne, formaty social media. Produkcja i postprodukcja dopasowana do platformy.',
    icon: `<svg viewBox="0 0 40 40" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><rect x="15" y="6" width="10" height="18" rx="5"/><path d="M9 19 a11 11 0 0 0 22 0"/><path d="M20 30 L20 34"/><path d="M14 34 L26 34"/></svg>`,
  },
  {
    num: '04',
    title: 'Postprodukcja',
    desc: 'Profesjonalny montaż i color grading powierzonych materiałów. Pracuję w DaVinci Resolve Studio.',
    icon: `<svg viewBox="0 0 40 40" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><circle cx="20" cy="20" r="13"/><path d="M20 7 a13 13 0 0 1 0 26"/><circle cx="20" cy="20" r="4" fill="currentColor" stroke="none"/></svg>`,
  },
]
</script>

<style scoped>
.services {
  padding: 5rem 3rem 3.5rem;
  background: var(--bg);
  position: relative;
}

.services-inner {
  max-width: 1200px;
  margin: 0 auto;
}

.services-head {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 2rem;
  flex-wrap: wrap;
  margin-bottom: 2.5rem;
}

.section-label {
  font-size: 0.6rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: var(--accent2);
  margin-bottom: 0.6rem;
}

h2 {
  font-family: var(--font-display);
  font-size: clamp(2.2rem, 4vw, 3.4rem);
  letter-spacing: 0.05em;
  color: var(--text);
  line-height: 1;
}

.services-tag {
  max-width: 360px;
  font-size: 0.82rem;
  line-height: 1.7;
  color: var(--muted);
  font-weight: 300;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1px;
  background: var(--border);
  border: 1px solid var(--border);
}

.service-card {
  padding: 2.4rem 2.2rem 2rem;
  background: var(--bg);
  transition: background 0.4s;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.service-card::before {
  content: '';
  position: absolute;
  left: 0; top: 0; right: 0;
  height: 2px;
  background: linear-gradient(to right, var(--accent), var(--accent2));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.55s cubic-bezier(0.4, 0, 0.2, 1);
}

.service-card::after {
  content: '';
  position: absolute;
  right: -60px; bottom: -60px;
  width: 200px; height: 200px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(201,75,40,0.18) 0%, transparent 70%);
  opacity: 0;
  transition: opacity 0.5s;
  pointer-events: none;
}

.service-card:hover { background: var(--surface); }
.service-card:hover::before { transform: scaleX(1); }
.service-card:hover::after { opacity: 1; }
.service-card:hover .service-icon { color: var(--accent); transform: translateY(-3px); }
.service-card:hover h3 { color: var(--accent2); }

.service-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 1.4rem;
}

.service-icon {
  width: 38px;
  height: 38px;
  color: var(--text);
  transition: color 0.35s, transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.service-num {
  font-family: var(--font-display);
  font-size: 0.8rem;
  color: var(--muted);
  letter-spacing: 0.24em;
  line-height: 1;
  padding: 0.35rem 0.7rem;
  border: 1px solid var(--border2);
}

h3 {
  font-family: var(--font-display);
  font-size: 1.35rem;
  font-weight: 400;
  color: var(--text);
  letter-spacing: 0.05em;
  text-transform: uppercase;
  line-height: 1.15;
  margin-bottom: 0.9rem;
  transition: color 0.3s;
}

p {
  font-size: 0.85rem;
  color: var(--muted);
  line-height: 1.75;
  font-weight: 300;
  flex-grow: 1;
  margin-bottom: 1.5rem;
}


/* Tools row */
.tools-row {
  margin-top: 3rem;
  padding-top: 2rem;
  border-top: 1px solid var(--border);
}

.tools-label {
  display: block;
  font-family: var(--font-display);
  font-size: 0.7rem;
  letter-spacing: 0.32em;
  text-transform: uppercase;
  color: var(--muted);
  margin-bottom: 1.4rem;
}

.tools-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 0.6rem;
}

.tool-chip {
  display: inline-flex;
  align-items: center;
  gap: 0.85rem;
  padding: 0.85rem 1.1rem;
  border: 1px solid var(--border2);
  transition: border-color 0.3s, transform 0.3s, background 0.3s;
  cursor: default;
}

.tool-chip:hover {
  border-color: var(--accent);
  transform: translateY(-2px);
  background: rgba(201,75,40,0.06);
}

.tool-cat {
  font-family: var(--font-body);
  font-size: 0.5rem;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: var(--accent2);
  display: block;
  margin-bottom: 3px;
}

.tool-name {
  font-family: var(--font-display);
  font-size: 0.82rem;
  letter-spacing: 0.1em;
  color: var(--text);
  line-height: 1.1;
}

.tool-name small {
  font-size: 0.55rem;
  letter-spacing: 0.22em;
  color: var(--muted);
  display: block;
  margin-top: 3px;
  font-family: var(--font-body);
  text-transform: uppercase;
}

.davinci-mark {
  display: inline-flex;
  align-items: center;
  flex-shrink: 0;
}

.davinci-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 12px rgba(201,75,40,0.7);
  animation: davinciPulse 2.4s ease-in-out infinite;
}

@keyframes davinciPulse {
  0%, 100% { box-shadow: 0 0 8px rgba(201,75,40,0.4); }
  50%       { box-shadow: 0 0 18px rgba(201,75,40,0.9); }
}

@media (max-width: 1024px) {
  .services { padding-left: 2.5rem; padding-right: 2.5rem; }
}

@media (max-width: 700px) {
  .services { padding-left: 1.5rem; padding-right: 1.5rem; }
  .services-grid { grid-template-columns: 1fr; }
  .service-card { padding: 1.8rem 1.5rem 1.6rem; }
}
</style>
