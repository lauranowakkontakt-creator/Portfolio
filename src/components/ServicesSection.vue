<template>
  <section class="services" id="services">
    <div class="services-inner">

      <div class="services-head reveal">
        <div>
          <p class="section-label">Usługi</p>
          <h2>Co robię?</h2>
        </div>
        <p class="services-tag">Przyjmuję zlecenia na każdym etapie — od pomysłu po gotowy plik.</p>
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
          <div class="service-tags">
            <span v-for="tag in service.tags" :key="tag" class="service-tag">{{ tag }}</span>
          </div>
        </div>
      </div>

      <div class="tools-row reveal reveal-delay-3">
        <span class="tools-label">Czym pracuję</span>
        <div class="tools-grid">
          <div class="tool-chip">
            <span class="tool-icon">
              <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round">
                <path d="M3 9 L9 9 L11 6 L19 6 L21 9 L27 9 L27 24 L3 24 Z"/>
                <circle cx="15" cy="16" r="5"/>
                <circle cx="15" cy="16" r="2.2" fill="currentColor"/>
                <rect x="22" y="11" width="3" height="1.5" rx="0.5" fill="currentColor" stroke="none"/>
              </svg>
            </span>
            <span class="tool-info">
              <span class="tool-cat">Kamera</span>
              <span class="tool-device">Panasonic Lumix S5IIX</span>
            </span>
          </div>
          <div class="tool-chip">
            <span class="tool-icon">
              <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="1.4">
                <circle cx="15" cy="15" r="11"/>
                <ellipse cx="15" cy="15" rx="11" ry="4.5"/>
                <ellipse cx="15" cy="15" rx="4.5" ry="11"/>
                <circle cx="15" cy="15" r="1.8" fill="currentColor"/>
              </svg>
            </span>
            <span class="tool-info">
              <span class="tool-cat">Kamera 360°</span>
              <span class="tool-device">Insta360 X4</span>
            </span>
          </div>
          <div class="tool-chip">
            <span class="tool-icon">
              <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="1.4">
                <circle cx="15" cy="15" r="11"/>
                <circle cx="15" cy="15" r="7"/>
                <circle cx="15" cy="15" r="3.5" fill="currentColor" fill-opacity="0.2"/>
                <path d="M15 4 L15 7 M15 23 L15 26 M4 15 L7 15 M23 15 L26 15" stroke-linecap="round"/>
              </svg>
            </span>
            <span class="tool-info">
              <span class="tool-cat">Obiektyw</span>
              <span class="tool-device">Sigma 24-70mm f/2.8 ART II</span>
            </span>
          </div>
          <div class="tool-chip">
            <span class="tool-icon">
              <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round">
                <path d="M15 3 L15 10"/>
                <rect x="11" y="7" width="8" height="4" rx="0.5"/>
                <path d="M15 11 L6 27"/>
                <path d="M15 11 L24 27"/>
                <path d="M15 11 L15 25"/>
                <path d="M4 27 L8 27 M13 25 L17 25 M22 27 L26 27"/>
              </svg>
            </span>
            <span class="tool-info">
              <span class="tool-cat">Statyw</span>
              <span class="tool-device">Manfrotto</span>
            </span>
          </div>
          <div class="tool-chip">
            <span class="tool-icon">
              <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round">
                <path d="M11 4 L19 4 L22 12 L22 18 L8 18 L8 12 Z"/>
                <path d="M15 18 L15 24"/>
                <path d="M11 26 L19 26"/>
                <path d="M12 8 L18 8 M12 11 L18 11 M12 14 L18 14" opacity="0.5"/>
              </svg>
            </span>
            <span class="tool-info">
              <span class="tool-cat">Światło</span>
              <span class="tool-device">Nanlite Forza 60B II</span>
            </span>
          </div>
          <div class="tool-chip">
            <span class="tool-icon">
              <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round">
                <rect x="6" y="6" width="18" height="18" rx="1"/>
                <path d="M6 11 L24 11 M6 16 L24 16 M6 21 L24 21"/>
                <circle cx="10" cy="8.5" r="1" fill="currentColor" stroke="none"/>
                <circle cx="15" cy="13.5" r="1" fill="currentColor" stroke="none"/>
                <circle cx="20" cy="18.5" r="1" fill="currentColor" stroke="none"/>
              </svg>
            </span>
            <span class="tool-info">
              <span class="tool-cat">Światło RGB</span>
              <span class="tool-device">Nanlite Litolite 5C RGB</span>
            </span>
          </div>
          <div class="tool-chip">
            <span class="tool-icon">
              <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round">
                <rect x="9" y="2" width="5" height="26" rx="2.5"/>
                <rect x="16" y="2" width="5" height="26" rx="2.5"/>
                <path d="M11.5 6 L11.5 24 M18.5 6 L18.5 24" opacity="0.45"/>
              </svg>
            </span>
            <span class="tool-info">
              <span class="tool-cat">Światło RGB</span>
              <span class="tool-device">Nanlite Pavotube II 30C × 2</span>
            </span>
          </div>
          <div class="tool-chip">
            <span class="tool-icon">
              <svg width="30" height="30" viewBox="0 0 30 30" fill="none" stroke="currentColor" stroke-width="1.4">
                <circle cx="15" cy="15" r="12"/>
                <path d="M15 3 a12 12 0 0 1 0 24" stroke="currentColor" stroke-width="1.4" fill="currentColor" fill-opacity="0.18"/>
                <circle cx="15" cy="15" r="4" fill="currentColor"/>
              </svg>
            </span>
            <span class="tool-info">
              <span class="tool-cat">Postprodukcja</span>
              <span class="tool-device">DaVinci Resolve Studio</span>
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
    title: 'Filmy ślubne & teledyski',
    desc: 'Wesela to spora część mojej pracy. Kręcę zarówno pełne filmy jak i krótkie teledyski — zależy co para chce zapamiętać. Dbam o emocje, nie tylko o ładne kadry.',
    tags: ['Film ślubny', 'Teledysk', 'Wesele'],
    icon: `<svg viewBox="0 0 40 40" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><path d="M14 28 L14 14 a6 6 0 0 1 12 0 L26 28"/><path d="M10 28 L30 28"/><circle cx="20" cy="14" r="2.5"/><path d="M20 16.5 L20 22"/></svg>`,
  },
  {
    num: '02',
    title: 'Studniówki & eventy',
    desc: 'Studniówki, koncerty, eventy firmowe. Wiem jak poruszać się z kamerą w tłumie i jak wyłapać momenty zanim znikną. Obsługa jednoosobowa lub z ekipą — do uzgodnienia.',
    tags: ['Studniówka', 'Event', 'Koncert'],
    icon: `<svg viewBox="0 0 40 40" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><rect x="4" y="12" width="22" height="16" rx="1"/><path d="M26 18 L36 13 L36 27 L26 22 Z"/><circle cx="10" cy="20" r="2"/></svg>`,
  },
  {
    num: '03',
    title: 'Muzyka, podcasty & social',
    desc: 'Teledyski muzyczne, nagrania podcastów, treści na social media. Produkcja i montaż w jednym — od ustawienia sprzętu po finalny plik gotowy do wrzucenia.',
    tags: ['Teledysk', 'Podcast', 'Reels'],
    icon: `<svg viewBox="0 0 40 40" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><rect x="15" y="6" width="10" height="18" rx="5"/><path d="M9 19 a11 11 0 0 0 22 0"/><path d="M20 30 L20 34"/><path d="M14 34 L26 34"/></svg>`,
  },
  {
    num: '04',
    title: 'Tylko montaż',
    desc: 'Masz już nakręcony materiał? Mogę go zmontować i wygradować. Pracuję w DaVinci Resolve Studio, więc kolor traktuję poważnie. Przyjmuję materiały z różnych kamer.',
    tags: ['Montaż', 'Color grading', 'DaVinci'],
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

.service-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.45rem;
}

.service-tag {
  font-family: var(--font-body);
  font-size: 0.55rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--muted);
  padding: 0.3rem 0.65rem;
  border: 1px solid var(--border2);
  transition: color 0.25s, border-color 0.25s;
}

.service-card:hover .service-tag {
  color: var(--accent2);
  border-color: rgba(201,75,40,0.35);
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
  gap: 0.95rem;
  padding: 0.95rem 1.1rem;
  border: 1px solid var(--border2);
  transition: border-color 0.3s, transform 0.3s, background 0.3s;
  cursor: default;
}

.tool-chip:hover {
  border-color: var(--accent);
  transform: translateY(-2px);
  background: rgba(201,75,40,0.06);
}

.tool-icon {
  width: 32px;
  height: 32px;
  flex-shrink: 0;
  color: var(--accent);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  transition: color 0.3s, transform 0.4s cubic-bezier(0.4,0,0.2,1);
}

.tool-chip:hover .tool-icon {
  color: var(--accent2);
  transform: rotate(-6deg) scale(1.08);
}

.tool-info {
  display: flex;
  flex-direction: column;
  gap: 3px;
}

.tool-cat {
  font-family: var(--font-display);
  font-size: 0.9rem;
  letter-spacing: 0.08em;
  color: var(--text);
  line-height: 1;
  text-transform: uppercase;
}

.tool-device {
  font-family: var(--font-body);
  font-size: 0.6rem;
  letter-spacing: 0.12em;
  color: var(--muted);
  line-height: 1;
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
