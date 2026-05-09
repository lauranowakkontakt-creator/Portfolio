<template>
  <section class="about" id="about">
    <div class="about-inner">
      <p class="section-label reveal">O mnie</p>
      <h2 class="reveal reveal-delay-1">7 lat w kadrze,<br>6 lat w montażowni.</h2>
      <p class="lead reveal reveal-delay-2">
        Ponad 200 domkniętych projektów. Moje doświadczenie to nie tylko liczby —
        to setki godzin na planach w najróżniejszych warunkach. Pracuję jako operatorka,
        montażystka i reżyserka. Koordynuję ekipy i prowadzę projekty od surowego pomysłu
        po finalny eksport.
      </p>

      <div class="pillars">
        <div v-for="(pillar, i) in pillars" :key="pillar.title" class="pillar reveal" :class="`reveal-delay-${i + 1}`">
          <span class="pillar-num">0{{ i + 1 }}</span>
          <p class="pillar-title">{{ pillar.title }}</p>
          <p class="pillar-text">{{ pillar.text }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const pillars = [
  {
    title: 'Psychologiczne podejście',
    text: 'Kończę studia psychologiczne, co w mojej pracy jest „supermocą". Rozumiem emocje na ekranie i dbam o te na planie. Buduję atmosferę, w której każdy czuje się swobodnie — co przekłada się na naturalne ujęcia.',
  },
  {
    title: 'Warsztat i narzędzia',
    text: 'Moim głównym środowiskiem jest DaVinci Resolve Studio. Sprawnie wdrażam narzędzia AI, które przyspieszają workflow, nie zabijając przy tym kreatywności.',
  },
  {
    title: 'Wszechstronność',
    text: 'Nieważne, czy to dynamiczny teledysk, intymny reportaż ślubny, czy techniczny podcast — adaptuję styl do Twojej wizji, zachowując najwyższą jakość detalu.',
  },
]
</script>

<style scoped>
.about {
  padding: 6rem 3rem;
  background: var(--surface);
}

.about-inner {
  max-width: 960px;
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
  font-size: clamp(2.2rem, 4vw, 3.5rem);
  letter-spacing: 0.05em;
  color: var(--text);
  line-height: 1;
  margin-bottom: 1.8rem;
}

.lead {
  font-size: 0.9rem;
  color: var(--muted);
  line-height: 1.9;
  max-width: 680px;
  margin-bottom: 3.5rem;
  font-weight: 300;
}

.pillars {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  border-top: 1px solid var(--border);
}

.pillar {
  padding: 2rem 2rem 2rem 0;
  border-right: 1px solid var(--border);
  transition: border-color 0.25s;
}

.pillar:hover { border-color: var(--border2); }

.pillar:last-child {
  border-right: none;
  padding-right: 0;
  padding-left: 2rem;
}

.pillar:not(:first-child):not(:last-child) {
  padding-left: 2rem;
}

.pillar-num {
  display: block;
  font-family: var(--font-display);
  font-size: 1.4rem;
  color: var(--accent);
  letter-spacing: 0.08em;
  margin-bottom: 0.8rem;
  line-height: 1;
}

.pillar-title {
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--text);
  letter-spacing: 0.03em;
  margin-bottom: 0.75rem;
}

.pillar-text {
  font-size: 0.82rem;
  color: var(--muted);
  line-height: 1.8;
  font-weight: 300;
}

@media (max-width: 1024px) {
  .about { padding-left: 2.5rem; padding-right: 2.5rem; }
}

@media (max-width: 700px) {
  .about { padding-left: 1.5rem; padding-right: 1.5rem; }
  .pillars { grid-template-columns: 1fr; }
  .pillar {
    padding: 1.5rem 0;
    border-right: none;
    border-bottom: 1px solid var(--border);
  }
  .pillar:last-child {
    padding-left: 0;
    border-bottom: none;
  }
  .pillar:not(:first-child):not(:last-child) {
    padding-left: 0;
  }
}
</style>
