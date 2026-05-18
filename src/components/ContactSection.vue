<template>
  <section class="contact" id="contact">
    <div class="contact-inner">
      <p class="section-label reveal">Kontakt</p>
      <h2 class="reveal reveal-delay-1">Pogadajmy.</h2>
      <p class="contact-desc reveal reveal-delay-2">
        Szukasz operatorki lub montażystki do projektu,
        albo interesuje Cię stała współpraca w produkcji czy postprodukcji?
      </p>
      <a href="mailto:laura.nowak.kontakt@gmail.com" class="contact-email reveal reveal-delay-3">
        laura.nowak.kontakt@gmail.com
      </a>
      <p class="contact-note reveal reveal-delay-4">Odpowiadam w ciągu 24h.</p>
      <p class="contact-location reveal reveal-delay-4">
        Gliwice & Śląsk — ale dla dobrego projektu wsiadam w auto.
      </p>
    </div>
  </section>
</template>

<style scoped>
.contact {
  padding: 7rem 3rem;
  background: var(--bg);
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  border-top: 1px solid var(--border);
}

.contact-inner {
  max-width: 600px;
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
  font-size: clamp(2.5rem, 5vw, 4.5rem);
  letter-spacing: 0.04em;
  color: var(--text);
  line-height: 1;
  margin-bottom: 1.5rem;
}

.contact-desc {
  color: var(--muted);
  font-size: 0.9rem;
  line-height: 1.9;
  max-width: 460px;
  margin-bottom: 3rem;
  font-weight: 300;
}

.contact-email {
  font-family: var(--font-display);
  font-size: clamp(1.1rem, 2.5vw, 1.8rem);
  letter-spacing: 0.06em;
  color: var(--text);
  text-decoration: none;
  border-bottom: 2px solid var(--accent);
  padding-bottom: 4px;
  transition: color 0.2s;
}

.contact-email:hover { color: var(--accent); }

.contact-note {
  margin-top: 1.5rem;
  font-size: 0.6rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--muted);
  opacity: 0.6;
}

.contact-location {
  margin-top: 0.6rem;
  font-size: 0.78rem;
  color: var(--muted);
  opacity: 0.5;
  font-weight: 300;
}

@media (max-width: 1024px) {
  .contact { padding-left: 2.5rem; padding-right: 2.5rem; }
}

@media (max-width: 700px) {
  .contact { padding-left: 1.5rem; padding-right: 1.5rem; }
}
</style>
