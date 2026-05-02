<template>
  <section class="contact" id="contact">
    <div class="contact-inner">
      <p class="section-label">Kontakt</p>
      <h2>Porozmawiajmy<br>o Twoim projekcie</h2>
      <p class="contact-desc">
        Planujesz ślub? Nagrywasz podcast? Szukasz kogoś, kto rozumie Twoją wizję
        i potrafi ją przełożyć na ekran? Napisz, chętnie porozmawiam.
      </p>
      <a href="mailto:laura.nowak.kontakt@gmail.com" class="contact-email">
        laura.nowak.kontakt@gmail.com
      </a>
      <p class="contact-note">Odpowiadam w ciągu 24 godzin</p>
    </div>
  </section>
</template>

<style scoped>
.contact {
  padding: 6rem 4rem;
  background: var(--bg);
  text-align: center;
}

.contact-inner {
  max-width: 600px;
  margin: 0 auto;
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
  font-size: clamp(2rem, 4vw, 3.2rem);
  color: var(--text);
  letter-spacing: -0.02em;
  line-height: 1.05;
  margin-bottom: 1.5rem;
}

.contact-desc {
  color: var(--muted);
  font-size: 0.95rem;
  line-height: 1.8;
  margin-bottom: 3rem;
}

.contact-email {
  display: inline-block;
  font-family: var(--font-display);
  font-size: clamp(1.1rem, 2.5vw, 1.6rem);
  font-weight: 600;
  color: var(--text);
  text-decoration: none;
  border-bottom: 2px solid var(--accent);
  padding-bottom: 4px;
  transition: color 0.25s, border-color 0.25s;
  letter-spacing: -0.01em;
}

.contact-email:hover {
  color: var(--accent);
}

.contact-note {
  margin-top: 1.5rem;
  font-size: 0.68rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--muted);
  opacity: 0.6;
}

@media (max-width: 1024px) {
  .contact { padding-left: 2.5rem; padding-right: 2.5rem; }
}

@media (max-width: 700px) {
  .contact { padding-left: 1.5rem; padding-right: 1.5rem; }
}
</style>
