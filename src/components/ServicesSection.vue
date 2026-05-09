<template>
  <section class="services" id="services">
    <div class="services-inner">
      <p class="section-label reveal">W czym mogę Ci pomóc?</p>
      <div class="services-grid">
        <div
          v-for="(service, i) in services"
          :key="service.title"
          class="service-card reveal"
          :class="`reveal-delay-${i + 1}`"
        >
          <span class="service-num">{{ service.num }}</span>
          <h3>{{ service.title }}</h3>
          <p>{{ service.desc }}</p>
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
  },
  {
    num: '02',
    title: 'Filmy Ślubne & Teledyski',
    desc: 'Emocje ujęte w nowoczesną formę. Dbam o każdy detal — od kompozycji kadru po rytm w montażu.',
  },
  {
    num: '03',
    title: 'Content Digitalowy',
    desc: 'Podcasty, nagrania muzyczne, formaty social media. Produkcja i postprodukcja dopasowana do platformy.',
  },
  {
    num: '04',
    title: 'Postprodukcja',
    desc: 'Profesjonalny montaż i color grading powierzonych materiałów. Pracuję w DaVinci Resolve Studio.',
  },
]
</script>

<style scoped>
.services {
  padding: 6rem 3rem;
  background: var(--bg);
}

.services-inner {
  max-width: 1100px;
}

.section-label {
  font-size: 0.6rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: var(--accent2);
  margin-bottom: 2.5rem;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  border-top: 1px solid var(--border);
  border-left: 1px solid var(--border);
}

.service-card {
  padding: 2.5rem;
  border-right: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  transition: border-color 0.25s, background 0.25s;
}

.service-card:hover {
  background: var(--surface);
  border-color: var(--border2);
}

.service-num {
  display: block;
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--accent);
  letter-spacing: 0.08em;
  margin-bottom: 1rem;
  line-height: 1;
}

h3 {
  font-size: 0.88rem;
  font-weight: 500;
  color: var(--text);
  letter-spacing: 0.04em;
  margin-bottom: 0.75rem;
  line-height: 1.3;
}

p {
  font-size: 0.82rem;
  color: var(--muted);
  line-height: 1.8;
  font-weight: 300;
}

@media (max-width: 1024px) {
  .services { padding-left: 2.5rem; padding-right: 2.5rem; }
}

@media (max-width: 700px) {
  .services { padding-left: 1.5rem; padding-right: 1.5rem; }
  .services-grid { grid-template-columns: 1fr; }
  .service-card { padding: 1.8rem 1.5rem; }
}
</style>
